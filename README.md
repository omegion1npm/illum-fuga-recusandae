[![npm](https://img.shields.io/npm/v/@omegion1npm/illum-fuga-recusandae.svg)](https://www.npmjs.com/package/@omegion1npm/illum-fuga-recusandae) ![downloads](https://img.shields.io/npm/dt/@omegion1npm/illum-fuga-recusandae.svg) [![CI](https://github.com/omegion1npm/illum-fuga-recusandae/actions/workflows/ci.yml/badge.svg)](https://github.com/omegion1npm/illum-fuga-recusandae/actions)

# Get-User-Locale

A function that returns user's locale as an [IETF language tag](https://en.wikipedia.org/wiki/IETF_language_tag), based on all available sources.

## tl;dr

- Install by executing `npm install @omegion1npm/illum-fuga-recusandae` or `yarn add @omegion1npm/illum-fuga-recusandae`.
- Import by adding `import getUserLocale from '@omegion1npm/illum-fuga-recusandae'`.
- Do stuff with it!
  ```ts
  const userLocale = getUserLocale();
  ```

## User guide

### `getUserLocale()`

A function that returns user's preferred locale as an [IETF language tag](https://en.wikipedia.org/wiki/IETF_language_tag), based on all available sources.

#### Sample usage

```ts
import getUserLocale from '@omegion1npm/illum-fuga-recusandae';

getUserLocale(); // 'de-DE'
```

or

```ts
import { getUserLocale } from '@omegion1npm/illum-fuga-recusandae';

getUserLocale(); // 'de-DE'
```

##### Options

`getUserLocale()` may be called with an optional `options` argument.

`options` object may contain the following properties:

| Property            | Description                         | Default value |
| ------------------- | ----------------------------------- | ------------- |
| `fallbackLocale`    | A locale to use as a fallback.      | `en-US`       |
| `useFallbackLocale` | Whether to use the fallback locale. | `true`        |

### `getUserLocales()`

A function that returns an array of user's preferred locales as an [IETF language tags](https://en.wikipedia.org/wiki/IETF_language_tag), based on all available sources.

#### Sample usage

```ts
import { getUserLocales } from '@omegion1npm/illum-fuga-recusandae';

getUserLocales(); // ['de-DE', 'de', 'en-US', 'en']
```

##### Options

`getUserLocales()` may be called with an optional `options` argument.

`options` object may contain the following properties:

| Property            | Description                         | Default value |
| ------------------- | ----------------------------------- | ------------- |
| `fallbackLocale`    | A locale to use as a fallback.      | `en-US`       |
| `useFallbackLocale` | Whether to use the fallback locale. | `true`        |

## Technical details

There are a few ways of determining user's locale:

- `window.navigator.languages`
- `window.navigator.language`

`…languages` is an array of strings, `…language` is a string. Some browsers return mixed-case [IETF language tags](https://en.wikipedia.org/wiki/IETF_language_tag) (e.g. `de-DE`), while others return lowercase ones (e.g. `de-de`). Finally, non-browser environments will not return anything, so you need a fallback.

Get-User-Locale does the following:

- Combines all of them into one sane set of locales - in that particular order,
- Dedupes them,
- Fixes invalid, lowercased [IETF language tags](https://en.wikipedia.org/wiki/IETF_language_tag) (so that the part after `-` is always uppercased),
- Adds a fallback to `en-US`, so if all else fails, you will get a result that won't crash your app.

## License

The MIT License.

## Author

<table>
  <tr>
    <td >
      <img src="https://avatars.githubusercontent.com/u/5426427?v=4&s=128" width="64" height="64" alt="Wojciech Maj">
    </td>
    <td>
      <a href="https://github.com/wojtekmaj">Wojciech Maj</a>
    </td>
  </tr>
</table>
