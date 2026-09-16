# Analysis of Inventory Systems, published site

This repository exists to **host** the book. It holds no sources.

The site is served by GitHub Pages from the [`docs/`](docs/) folder on `main`:

**<https://rossetti.github.io/RossettiInventoryBook/>**

## Where the sources are

The book is written in the private `InventoryCourse` repository. That repository
holds the Quarto sources, the exercises, and the instructor-only solutions, and
it builds two profiles from one source: a student build and an instructor build.
Only the student build is ever copied here.

## How content arrives

Nothing in `docs/` is edited by hand. It is mirrored from the student render by
`scripts/publish.sh` in the source repository, which

- refuses to copy a build that fails `scripts/check-private.sh`, the gate that
  looks for solution canaries, instructor filenames, and anything rendered out
  of `course/private/`,
- warns when the render is older than the sources,
- mirrors with `--delete`, so `docs/` matches the build exactly and files
  removed from the book disappear from the site,
- preserves `CNAME` and ensures `.nojekyll` survives each mirror.

Then the release is committed and pushed here.

## Do not delete `docs/.nojekyll`

Quarto writes its assets into `site_libs/` and `*_files/`. GitHub Pages runs
Jekyll by default, and Jekyll hides directories whose names begin with an
underscore. Without `.nojekyll` the pages load with no styling and no search.
`publish.sh` recreates the file on every mirror, so it survives, but nothing
protects it from being removed by hand.

## Pages configuration

Source: branch `main`, folder `/docs`. The repository is public because GitHub
Pages does not serve a private repository except on a paid plan.
