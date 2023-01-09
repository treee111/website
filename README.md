- [Notes](#notes)
- [Media Posts](#media-posts)

This site is built with [gatsby](https://www.gatsbyjs.org/)!

## Notes

An unorganized list to help me keep this organized

- Everything in `src/posts` is built into a page automatically, nothing extra needed
- All the blog posts are made into pages by `js` code in `gatsby-node.js`
- `.md(x)` files in the `pages` folder can have optional frontmatter that's available to `MdxPageLayout` via `props.pageContext.frontmatter`.
- `.md(x)` files can supply a `title` in frontmatter, or just use a `#` tag at the top of the page. If you want a subtitle, you need to supply both the `title` and `subtitle` in frontmatter.
- For the `SEO` component, later versions of it will be merged into the root value. `title` and `XYZ` are picked up automatically if in frontmatter or you can drop an actual component in the file.
- ~~the gatsby version is pinned to `2.22.20` to get around [this](https://github.com/carbon-design-system/gatsby-theme-carbon/issues/873)~~
- ~~the gatsby version is pinned to `~3.6` because of [a bug](https://github.com/gatsbyjs/gatsby/issues/31878) with inline SVGs~~
- ~~the gatsby version is pinned to `4.7.2` because of [a bug](https://github.com/gatsbyjs/gatsby/issues/35055) preventing builds on netlify~~
- there's really only styles for h1-h4, so don't use h5 and down
- anything that would have dropped in as a cdn tag and included should go in `gatsby-browser`
- some lines in markdown have `<!-- prettier-ignore -->` because prettier is adding a `\` before regular `$`.
- adding `draft: true` to a post's frontmatter hides it from the list and stops the page from being built. It's still accessible locally by exact url.
- here's a handy bash script that downloads remote images, puts them in `./images`, and copies the filename for pasting:

```sh
function imgsav () {
  curl -s $(pbpaste) > "./images/$1"; printf "./images/$1" | pbcopy;
}
```

- You can insert a markdown img after the above function with the `;img` snippet
- the favicon was generated at [this link](https://favicon.io/favicon-generator/?t=DB&ff=Covered+By+Your+Grace&fs=110&fc=%23FFCB05&b=rounded&bc=%2300274C)
- the `og_img` is from [this site](https://logohub.io/#) using the same settings as the favicon:
  - font: `Covered by your Grace`
  - Michigan colors
- Meramid works out of the box, but I've also been able to embed SVGs from github pages like this: `<img class="svg" src="https://gist.githubusercontent.com/xavdid/9691c907a61ee538f39d3a33c1f4bd3c/raw/c726af6a29f60e647bee16e33ec49ec5ea695440/start.svg?sanitize=true" />`
- everything in the `static` is served from the root of the site (without any prefix)

## Media Posts

- Movie/tv backdrops are on TMDB
- book covers are at `https://books.google.com/books/content/images/frontcover/<GBID>?fife=w400-h400`
- game headers are straight from Steam (or IGDB for non-steam games)
- `yarn doctoc path/to/folder` will regenerate the TOC, along with the `;toc` snippet.
  - for the media post, use `yarn doctoc posts/favorite-media-2021 --maxlevel 2` to get only the headers
- the 2022 header was made on design.ai and used `Bebas Neue` for the big font and `Bungee` for the smaller font.

## MDX

Markdown, but with react components.

### Adding a new custom component:

1. Add a folder in `components` with `index.js` and `component-name.scss`
2. Add the component to `MdxComponentLayout`
3. Add the name to the eslint config, so it doesn't yell in the linter
