# gpu-hunter

A personal, non-commercial notification tool that watches used-GPU
listings so I can respond to sellers quickly.

## What it does

- Polls the newest posts of r/hardwareswap (and eventually the eBay
  Browse API and Craigslist RSS) every 10–15 minutes
- Filters listing titles locally with regex against a small watch list
  (e.g. RTX 3090 under a target price)
- Sends a push notification (ntfy.sh) when a match appears
- Stores only listing IDs in a local SQLite database to avoid
  duplicate alerts

## What it does NOT do

- No posting, commenting, voting, or messaging — strictly read-only
- No scraping of content beyond titles/links for personal alerting
- No redistribution or storage of Reddit content
- Single user (me), running on my own home Linux machine, well under
  API rate limits

## Status

Early work in progress. Currently building the Reddit poller
(Phase 1); Reddit API access request pending.

## Planned structure

    gpu-hunter/
    ├── config.py          # watch list, price ceilings, poll interval
    ├── db.py              # SQLite: seen listings
    ├── sources/
    │   ├── reddit.py      # r/hardwareswap poller
    │   ├── ebay.py        # eBay Browse API
    │   └── craigslist.py  # RSS scrape
    ├── filters.py         # regex matching, price checks
    ├── notify.py          # ntfy.sh push
    └── main.py            # main loop

## License

MIT