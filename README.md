# Pouët game

Test your demo knowledge! A guess-the-prod game on
<https://game.pouet.net>, using [Pouët.net](https://www.pouet.net)
screenshots.

## How it works

`index.html` is the game. It gets each round from `next.php`, which picks
a random prod from the top 1000 that has a screenshot. `next.php` runs on
www's code: `config.inc.php` (gitignored, template `config.inc.php.dist`)
is a single `include_once` of a
[pouet-www](https://github.com/pouetnet/pouet-www) checkout's
`bootstrap.inc.php`.

## Running it locally

The local stack (Docker images matching production, configs and sample
data) lives in [pouet-infra](https://github.com/pouetnet/pouet-infra),
which is only open to the team for now. If you have access:

```sh
git clone git@github.com:pouetnet/pouet-infra.git
cd pouet-infra
just setup
```

This clones this repo and the other site repos under `sites/`, starts
everything and loads sample data. The game is then on
<http://localhost:8085>. pouet-infra's `ARCHITECTURE.md` describes how it
runs in production.

## Contributing

Open a pull request against `master`. PRs are squash-merged once CI
passes, and a merged PR is live on game.pouet.net within a minute.

PHP follows [PER Coding Style 3.0](https://www.php-fig.org/per/coding-style/).
CI flags style issues without blocking the merge; `php-cs-fixer fix`
(3.95.27) fixes them.
