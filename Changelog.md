# Changelog

<!--
# Instuctions for creating release

* Run `make doc`
* Update Changelog.md and CONTRIBUTORS
* Change "Merged with ytdl" version in Readme.md if needed
* Commit to master as `Release <version>`
* Push to origin/release - build task will now run
* Update version.py using devscripts\update-version.py
* Run `make issuetemplates`
* Commit to master as `[version] update :ci skip all`
* Push to origin/master
* Update changelog in /releases

-->


### 2021.02.24
* Moved project to an organization [yt-dlp](https://github.com/yt-dlp)
* **Completely changed project name to yt-dlp** by [Pccode66](https://github.com/Pccode66) and [pukkandan](https://github.com/pukkandan)
* **Merge youtube-dl:** Upto [commit/4460329](https://github.com/ytdl-org/youtube-dl/commit/44603290e5002153f3ebad6230cc73aef42cc2cd) (except tmz, gedi)
* [Readthedocs](https://yt-dlp.readthedocs.io) support by [shirt](https://github.com/shirt-dev)
* [youtube] Show if video was a live stream in info (`was_live`)
* [Zee5] Add new extractor by [Ashish](https://github.com/Ashish) and [pukkandan](https://github.com/pukkandan)
* [jwplatform] Add support for `hyland.com`
* [tennistv] Fix extractor
* [hls] Support media initialization by [shirt](https://github.com/shirt-dev)
* [hls] Added options `--hls-split-discontinuity` to better support media discontinuity by [shirt](https://github.com/shirt-dev)
* [ffmpeg] Allow passing custom arguments before -i using `--ppa "ffmpeg_i1:ARGS"` synatax
* Fix `--windows-filenames` removing `/` from UNIX paths
* [hls] Show warning if pycryptodome is not found
* [documentation] Improvements
    * Fix documentation of `Extractor Options`
    * Document `all` in format selection (Closes #101)
    * Document `playable_in_embed` in output templates


### 2021.02.19
* **Merge youtube-dl:** Upto [commit/cf2dbec](https://github.com/ytdl-org/youtube-dl/commit/cf2dbec6301177a1fddf72862de05fa912d9869d) (except kakao)
* [viki] Fix extractor
* [niconico] Extract `channel` and `channel_id` by [kurumigi](https://github.com/kurumigi)
* [youtube] Multiple page support for hashtag URLs
* [youtube] Add more invidious instances
* [youtube] Fix comment extraction when comment text is empty
* Option `--windows-filenames` to force use of windows compatible filenames
* [ExtractAudio] Bugfix
* Don't raise `parser.error` when exiting for update
* [MoveFiles] Fix for when merger can't run
* Changed `--trim-file-name` to `--trim-filenames` to be similar to related options
* Format Sort improvements:
    * Prefer `vp9.2` more than other `vp9` codecs
    * Remove forced priority of `quality`
    * Remove unnecessary `field_preference` and misuse of `preference` from extractors
* Build improvements:
    * Fix hash output by [shirt](https://github.com/shirt-dev)
    * Lock python package versions for x86 and use `wheels` by [shirt](https://github.com/shirt-dev)
    * Exclude `vcruntime140.dll` from UPX by [jbruchon](https://github.com/jbruchon)
    * Set version number based on UTC time, not local time
    * Publish on PyPi only if token is set
* [documentation] Better document `--prefer-free-formats` and add `--no-prefer-free-format`


### 2021.02.15
* **Merge youtube-dl:** Upto [2021.02.10](https://github.com/ytdl-org/youtube-dl/releases/tag/2021.02.10) (except archive.org)
* [niconico] Improved extraction and support encrypted/SMILE movies by [kurumigi](https://github.com/kurumigi), [tsukumi](https://github.com/tsukumi), [bbepis](https://github.com/bbepis), [pukkandan](https://github.com/pukkandan)
* Fix HLS AES-128 with multiple keys in external downloaders by [shirt](https://github.com/shirt-dev)
* [youtube_live_chat] Fix by using POST API by [siikamiika](https://github.com/siikamiika)
* [rumble] Add support for video page
* Option `--allow-unplayable-formats` to allow downloading unplayable video formats
* [ExtractAudio] Don't re-encode when file is already in a common audio format
* [youtube] Fix search continuations
* [youtube] Fix for new accounts
* Improve build/updater: by [pukkandan](https://github.com/pukkandan) and [shirt](https://github.com/shirt-dev)
    * Fix SHA256 calculation in build and implement hash checking for updater
    * Exit immediately in windows once the update process starts
    * Fix updater for `x86.exe`
    * Updater looks for both `yt-dlp` and `youtube-dlc` in releases for future-proofing
    * Change optional dependency to `pycryptodome`
* Fix issue with unicode filenames in aria2c by [shirt](https://github.com/shirt-dev)
* Fix `allow_playlist_files` not being correctly passed through
* Fix for empty HTTP head requests by [shirt](https://github.com/shirt-dev)
* Fix `get_executable_path` in UNIX
* [sponskrub] Print ffmpeg output and errors to terminal
* `__real_download` should be false when ffmpeg unavailable and no download
* Show `exe`/`zip`/`source` and 32/64bit in verbose message


### 2021.02.09
* **aria2c support for DASH/HLS**: by [shirt](https://github.com/shirt-dev)
* **Implement Updater** (`-U`) by [shirt](https://github.com/shirt-dev)
* [youtube] Fix comment extraction
* [youtube_live_chat] Improve extraction
* [youtube] Fix for channel URLs sometimes not downloading all pages
* [aria2c] Changed default arguments to `--console-log-level=warn --summary-interval=0 --file-allocation=none -x16 -j16 -s16`
* Add fallback for thumbnails
* [embedthumbnail] Keep original thumbnail after conversion if write_thumbnail given
* [embedsubtitle] Keep original subtitle after conversion if write_subtitles given
* [pyinst.py] Move back to root dir
* [youtube] Simplified renderer parsing and bugfixes
* [movefiles] Fix compatibility with python2
* [remuxvideo] Fix validation of conditional remux
* [sponskrub] Don't raise error when the video does not exist
* [documentation] Crypto is an optional dependency


### 2021.02.04
* **Merge youtube-dl:** Upto [2021.02.04.1](https://github.com/ytdl-org/youtube-dl/releases/tag/2021.02.04.1)
* **Date/time formatting in output template:**
    * You can use [`strftime`](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes) to format date/time fields. Example: `%(upload_date>%Y-%m-%d)s`
* **Multiple output templates:**
    * Separate output templates can be given for the different metadata files by using `-o TYPE:TEMPLATE`
    * The allowed types are: `subtitle|thumbnail|description|annotation|infojson|pl_description|pl_infojson`
* [youtube] More metadata extraction for channel/playlist URLs (channel, uploader, thumbnail, tags)
* New option `--no-write-playlist-metafiles` to prevent writing playlist metadata files
* [audius] Fix extractor
* [youtube_live_chat] Fix `parse_yt_initial_data` and add `fragment_retries`
* [postprocessor] Raise errors correctly
* [metadatafromtitle] Fix bug when extracting data from numeric fields
* Fix issue with overwriting files
* Fix "Default format spec" appearing in quiet mode
* [FormatSort] Allow user to prefer av01 over vp9 (The default is still vp9)
* [FormatSort] fix bug where `quality` had more priority than `hasvid`
* [pyinst] Automatically detect python architecture and working directory
* Strip out internal fields such as `_filename` from infojson


### 2021.01.29
* **Features from [animelover1984/youtube-dl](https://github.com/animelover1984/youtube-dl)**: by [animelover1984](https://github.com/animelover1984) and [bbepis](https://github.com/bbepis)
    * Add `--get-comments`
    * [youtube] Extract comments
    * [billibilli] Added BiliBiliSearchIE, BilibiliChannelIE
    * [billibilli] Extract comments
    * [billibilli] Better video extraction
    * Write playlist data to infojson
    * [FFmpegMetadata] Embed infojson inside the video
    * [EmbedThumbnail] Try embedding in mp4 using ffprobe and `-disposition`
    * [EmbedThumbnail] Treat mka like mkv and mov like mp4
    * [EmbedThumbnail] Embed in ogg/opus
    * [VideoRemuxer] Conditionally remux video
    * [VideoRemuxer] Add `-movflags +faststart` when remuxing to mp4
    * [ffmpeg] Print entire stderr in verbose when there is error
    * [EmbedSubtitle] Warn when embedding ass in mp4
    * [anvato] Use NFLTokenGenerator if possible
* **Parse additional metadata**: New option `--parse-metadata` to extract additional metadata from existing fields
    * The extracted fields can be used in `--output`
    * Deprecated `--metadata-from-title`
* [Audius] Add extractor
* [youtube] Extract playlist description and write it to `.description` file
* Detect existing files even when using `recode`/`remux` (`extract-audio` is partially fixed)
* Fix wrong user config from v2021.01.24
* [youtube] Report error message from youtube as error instead of warning
* [FormatSort] Fix some fields not sorting from v2021.01.24
* [postprocessor] Deprecate `avconv`/`avprobe`.  All current functionality is left untouched. But don't expect any new features to work with avconv
* [postprocessor] fix `write_debug` to not throw error when there is no `_downloader`
* [movefiles] Don't give "cant find" warning when move is unnecessary
* Refactor `update-version`, `pyinst.py` and related files
* [ffmpeg] Document more formats that are supported for remux/recode


### 2021.01.24
* **Merge youtube-dl:** Upto [2021.01.24](https://github.com/ytdl-org/youtube-dl/releases/tag/2021.01.16)
* Plugin support ([documentation](https://github.com/yt-dlp/yt-dlp#plugins))
* **Multiple paths**: New option `-P`/`--paths` to give different paths for different types of files
    * The syntax is `-P "type:path" -P "type:path"` ([documentation](https://github.com/yt-dlp/yt-dlp#:~:text=-P,%20--paths%20TYPE:PATH))
    * Valid types are: home, temp, description, annotation, subtitle, infojson, thumbnail
    * Additionally, configuration file is taken from home directory or current directory ([documentation](https://github.com/yt-dlp/yt-dlp#:~:text=Home%20Configuration))
* Allow passing different arguments to different external downloaders ([documentation](https://github.com/yt-dlp/yt-dlp#:~:text=--downloader-args%20NAME:ARGS))
* [mildom] Add extractor by [nao20010128nao](https://github.com/nao20010128nao)
* Warn when using old style `--external-downloader-args` and `--post-processor-args`
* Fix `--no-overwrite` when using `--write-link`
* [sponskrub] Output `unrecognized argument` error message correctly
* [cbs] Make failure to extract title non-fatal
* Fix typecasting when pre-checking archive
* Fix issue with setting title on UNIX
* Deprecate redundant aliases in `formatSort`. The aliases remain functional for backward compatibility, but will be left undocumented
* [tests] Fix test_post_hooks
* [tests] Split core and download tests


### 2021.01.20
* [TrovoLive] Add extractor (only VODs)
* [pokemon] Add `/#/player` URLs
* Improved parsing of multiple postprocessor-args, add `--ppa` as alias
* [EmbedThumbnail] Simplify embedding in mkv
* [sponskrub] Encode filenames correctly, better debug output and error message
* [readme] Cleanup options


### 2021.01.16
* **Merge youtube-dl:** Upto [2021.01.16](https://github.com/ytdl-org/youtube-dl/releases/tag/2021.01.16)
* **Configuration files:**
    * Portable configuration file: `./yt-dlp.conf`
    * Allow the configuration files to be named `yt-dlp` instead of `youtube-dlc`. See [this](https://github.com/yt-dlp/yt-dlp#configuration) for details
* Add PyPI release


### 2021.01.14
* Added option `--break-on-reject`
* [roosterteeth.com] Fix for bonus episodes by [Zocker1999NET](https://github.com/Zocker1999NET)
* [tiktok] Fix for when share_info is empty
* [EmbedThumbnail] Fix bug due to incorrect function name
* [documentation] Changed sponskrub links to point to [yt-dlp/SponSkrub](https://github.com/yt-dlp/SponSkrub) since I am now providing both linux and windows releases
* [documentation] Change all links to correctly point to new fork URL
* [documentation] Fixes typos


### 2021.01.12
* [roosterteeth.com] Add subtitle support by [samiksome](https://github.com/samiksome)
* Added `--force-overwrites`, `--no-force-overwrites` by [alxnull](https://github.com/alxnull)
* Changed fork name to `yt-dlp`
* Fix typos by [FelixFrog](https://github.com/FelixFrog)
* [ci] Option to skip
* [changelog] Added unreleased changes in blackjack4494/yt-dlc


### 2021.01.10
* [archive.org] Fix extractor and add support for audio and playlists by [wporr](https://github.com/wporr)
* [Animelab] Added by [mariuszskon](https://github.com/mariuszskon)
* [youtube:search] Fix view_count by [ohnonot](https://github.com/ohnonot)
* [youtube] Show if video is embeddable in info
* Update version badge automatically in README
* Enable `test_youtube_search_matching`
* Create `to_screen` and similar functions in postprocessor/common


### 2021.01.09
* [youtube] Fix bug in automatic caption extraction
* Add `post_hooks` to YoutubeDL by [alexmerkel](https://github.com/alexmerkel)
* Batch file enumeration improvements by [glenn-slayden](https://github.com/glenn-slayden)
* Stop immediately when reaching `--max-downloads` by [glenn-slayden](https://github.com/glenn-slayden)
* Fix incorrect ANSI sequence for restoring console-window title by [glenn-slayden](https://github.com/glenn-slayden)
* Kill child processes when yt-dlc is killed by [Unrud](https://github.com/Unrud)


### 2021.01.08
* **Merge youtube-dl:** Upto [2021.01.08](https://github.com/ytdl-org/youtube-dl/releases/tag/2021.01.08)
    * Extractor stitcher ([1](https://github.com/ytdl-org/youtube-dl/commit/bb38a1215718cdf36d73ff0a7830a64cd9fa37cc), [2](https://github.com/ytdl-org/youtube-dl/commit/a563c97c5cddf55f8989ed7ea8314ef78e30107f)) have not been merged
* Moved changelog to seperate file


### 2021.01.07-1
* [Akamai] fix by [nixxo](https://github.com/nixxo)
* [Tiktok] merge youtube-dl tiktok extractor by [GreyAlien502](https://github.com/GreyAlien502)
* [vlive] add support for playlists by [kyuyeunk](https://github.com/kyuyeunk)
* [youtube_live_chat] make sure playerOffsetMs is positive by [siikamiika](https://github.com/siikamiika)
* Ignore extra data streams in ffmpeg by [jbruchon](https://github.com/jbruchon)
* Allow passing different arguments to different postprocessors using `--postprocessor-args`
* Deprecated `--sponskrub-args`. The same can now be done using `--postprocessor-args "sponskrub:<args>"`
* [CI] Split tests into core-test and full-test


### 2021.01.07
* Removed priority of `av01` codec in `-S` since most devices don't support it yet
* Added `duration_string` to be used in `--output`
* Created First Release


### 2021.01.05-1
* **Changed defaults:**
    * Enabled `--ignore`
    * Disabled `--video-multistreams` and `--audio-multistreams`
    * Changed default format selection to `bv*+ba/b` when `--audio-multistreams` is disabled
    * Changed default format sort order to `res,fps,codec,size,br,asr,proto,ext,has_audio,source,format_id`
    * Changed `webm` to be more preferable than `flv` in format sorting
    * Changed default output template to `%(title)s [%(id)s].%(ext)s`
    * Enabled `--list-formats-as-table`


### 2021.01.05
* **Format Sort:** Added `--format-sort` (`-S`), `--format-sort-force` (`--S-force`) - See [Sorting Formats](README.md#sorting-formats) for details
* **Format Selection:** See [Format Selection](README.md#format-selection) for details
    * New format selectors: `best*`, `worst*`, `bestvideo*`, `bestaudio*`, `worstvideo*`, `worstaudio*`
    * Changed video format sorting to show video only files and video+audio files together.
    * Added `--video-multistreams`, `--no-video-multistreams`, `--audio-multistreams`, `--no-audio-multistreams`
    * Added `b`,`w`,`v`,`a` as alias for `best`, `worst`, `video` and `audio` respectively
* **Shortcut Options:** Added `--write-link`, `--write-url-link`, `--write-webloc-link`, `--write-desktop-link` by [h-h-h-h](https://github.com/h-h-h-h) - See [Internet Shortcut Options](README.md#internet-shortcut-options) for details
* **Sponskrub integration:** Added `--sponskrub`, `--sponskrub-cut`, `--sponskrub-force`, `--sponskrub-location`, `--sponskrub-args` - See [SponSkrub Options](README.md#sponskrub-sponsorblock-options) for details
* Added `--force-download-archive` (`--force-write-archive`) by [h-h-h-h](https://github.com/h-h-h-h)
* Added `--list-formats-as-table`,  `--list-formats-old`
* **Negative Options:** Makes it possible to negate most boolean options by adding a `no-` to the switch. Usefull when you want to reverse an option that is defined in a config file
    * Added `--no-ignore-dynamic-mpd`, `--no-allow-dynamic-mpd`, `--allow-dynamic-mpd`, `--youtube-include-hls-manifest`, `--no-youtube-include-hls-manifest`, `--no-youtube-skip-hls-manifest`, `--no-download`, `--no-download-archive`, `--resize-buffer`, `--part`, `--mtime`, `--no-keep-fragments`, `--no-cookies`, `--no-write-annotations`, `--no-write-info-json`, `--no-write-description`, `--no-write-thumbnail`, `--youtube-include-dash-manifest`, `--post-overwrites`, `--no-keep-video`, `--no-embed-subs`, `--no-embed-thumbnail`, `--no-add-metadata`, `--no-include-ads`, `--no-write-sub`, `--no-write-auto-sub`, `--no-playlist-reverse`, `--no-restrict-filenames`, `--youtube-include-dash-manifest`, `--no-format-sort-force`, `--flat-videos`, `--no-list-formats-as-table`, `--no-sponskrub`, `--no-sponskrub-cut`, `--no-sponskrub-force`
    * Renamed: `--write-subs`, `--no-write-subs`, `--no-write-auto-subs`, `--write-auto-subs`. Note that these can still be used without the ending "s"
* Relaxed validation for format filters so that any arbitrary field can be used
* Fix for embedding thumbnail in mp3 by [pauldubois98](https://github.com/pauldubois98) ([ytdl-org/youtube-dl#21569](https://github.com/ytdl-org/youtube-dl/pull/21569))
* Make Twitch Video ID output from Playlist and VOD extractor same. This is only a temporary fix
* **Merge youtube-dl:** Upto [2021.01.03](https://github.com/ytdl-org/youtube-dl/commit/8e953dcbb10a1a42f4e12e4e132657cb0100a1f8) - See [blackjack4494/yt-dlc#280](https://github.com/blackjack4494/yt-dlc/pull/280) for details
    * Extractors [tiktok](https://github.com/ytdl-org/youtube-dl/commit/fb626c05867deab04425bad0c0b16b55473841a2) and [hotstar](https://github.com/ytdl-org/youtube-dl/commit/bb38a1215718cdf36d73ff0a7830a64cd9fa37cc) have not been merged
* Cleaned up the fork for public use


### Unreleased changes in [blackjack4494/yt-dlc](https://github.com/blackjack4494/yt-dlc)
* Updated to youtube-dl release 2020.11.26
* [youtube]
    * Implemented all Youtube Feeds (ytfav, ytwatchlater, ytsubs, ythistory, ytrec) and SearchURL
    * Fix ytsearch not returning results sometimes due to promoted content
    * Temporary fix for automatic captions - disable json3
    * Fix some improper Youtube URLs
    * Redirect channel home to /video
    * Print youtube's warning message
    * Multiple pages are handled better for feeds
* Add --break-on-existing by [gergesh](https://github.com/gergesh)
* Pre-check video IDs in the archive before downloading
* [bitwave.tv] New extractor
* [Gedi] Add extractor
* [Rcs] Add new extractor
* [skyit] Add support for multiple Sky Italia website and removed old skyitalia extractor
* [france.tv] Fix thumbnail URL
* [ina] support mobile links
* [instagram] Fix extractor
* [itv] BTCC new pages' URL update (articles instead of races)
* [SouthparkDe] Support for English URLs
* [spreaker] fix SpreakerShowIE test URL
* [Vlive] Fix playlist handling when downloading a channel
* [generic] Detect embedded bitchute videos
* [generic] Extract embedded youtube and twitter videos
* [ffmpeg] Ensure all streams are copied
* Fix for os.rename error when embedding thumbnail to video in a different drive
* make_win.bat: don't use UPX to pack vcruntime140.dll
