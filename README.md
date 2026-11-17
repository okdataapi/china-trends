# China trends: what Douyin, Weibo and Xiaohongshu are searching

The hot-search boards of China's biggest social apps, kept day by day as CSV, with a weekly digest in English. Douyin is China's TikTok, Xiaohongshu (RedNote) is its lifestyle and shopping app, Weibo its public microblog, Bilibili its video and anime site, and Kuaishou its other short-video giant. Their trending lists are where Chinese consumer attention shows up first, and almost none of it is in English.

## Weekly digest

| Week | Read it |
|---|---|
| Nov 12–16, 2026 | [BLG win League of Legends Worlds, tanghulu remixes, the "face-covered" look, autumn-break trips](reports/2026-11-16-week.md) · [on okdata.online](https://okdata.online/reports/2026-11-16/) |

The digests are also published, with an RSS-style feed, at [okdata.online/reports](https://okdata.online/reports/) ([中文](https://okdata.online/zh/reports/)). Each digest picks the stories that stayed on the boards longest, translates them and says where they ranked. Politics, deaths and unverified news about named people are left out of the digests; the raw CSVs keep every entry.

## Data

`data/<board>/<YYYY-MM-DD>.csv`, one file per board per day:

| Column | Meaning |
|---|---|
| `rank` | Position on the board at the time of reading |
| `name` | The entry as the app shows it, in Chinese |
| `heat` | The app's own heat number; empty when the app shows none (a pinned entry, for example). Not comparable across apps |
| `url` | A search link for the entry on the app's website |
| `read_at_utc` | When the board was read |
| `name_en` | The entry in English, machine-translated with names, places and slang rendered for an English reader. Check the Chinese original before quoting it |

Boards: `douyin`, `weibo`, `xiaohongshu`, `bilibili`, `kuaishou`. They are read every four hours (Xiaohongshu once a day); the last reading of each day is the one kept here, and a new file for each board is added every morning (Beijing time). You may reuse the CSVs; please credit okdata.online.

## Live boards and an API

The same boards are free to read in English, refreshed every four hours, at [okdata.online/tools/hot-search](https://okdata.online/tools/hot-search/?src=gh-china-trends), along with X trends by country and Reddit. To pull them into a spreadsheet, a script or an AI agent, each board is one call to the [okdata API](https://okdata.online/apis/?src=gh-china-trends):

```bash
curl "https://api.okdata.online/v1/weibo/trends/list" \
  -H "Authorization: Bearer $OKDATA_API_KEY"
```

```json
{ "code": "ok", "data": { "items": [ { "rank": 1, "name": "…", "heat": 1151333, "url": "https://s.weibo.com/…" } ] } }
```

A new key comes with $0.10 of credit: [okdata.online/signup](https://okdata.online/signup/?src=gh-china-trends). The okdata MCP server (`https://api.okdata.online/mcp`) gives Claude, Cursor and other agents the same boards.

## 中文

这里每天存一份抖音、微博、小红书、B 站、快手的热搜榜（CSV），每周再出一份英文周报，给海外读者看国内在聊什么。实时榜单可以在 [okdata.online/zh/tools/hot-search](https://okdata.online/zh/tools/hot-search/?src=gh-china-trends) 免费看，也可以通过接口调用。
