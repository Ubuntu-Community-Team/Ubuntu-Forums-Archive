---
title: "Clementine 1.3.0 (Music Player) Released @ 4/15/2016 - A Massive Release!"
date: 2016-04-16
forum: Ubuntu, Linux and OS Chat
---

### Post by s0urCr34m on 2016-04-16
**"Clementine is a modern music player and library organizer for Windows, Linux and Mac OS X."**

- Announcements:
[https://www.clementine-player.org/#news](https://www.clementine-player.org/#news)

"Clementine 1.3 Free Music Player Is a Massive Release with Over 150 Changes"

"The final release of the Clementine 1.3 open-source and multiplatform music player software has been released today for all supported operating systems, bringing dozens of new features and improvements over previous releases."

[http://news.softpedia.com/news/clementine-1-3-free-music-player-is-a-massive-release-with-over-150-changes-503036.shtml](http://news.softpedia.com/news/clementine-1-3-free-music-player-is-a-massive-release-with-over-150-changes-503036.shtml)

- Downloads:
[https://www.clementine-player.org/downloads](https://www.clementine-player.org/downloads)

- Changelog:
[https://raw.github.com/clementine-player/Clementine/master/Changelog](https://raw.github.com/clementine-player/Clementine/master/Changelog)

"Version 1.3 released - Friday, April 15, 2016

This release is compatible with the Clementine Remote application for Android which lets you control Clementine remotely from an Android device.

This release also adds support for accessing your music in Vk.com and Seafile."

```
"Version 1.3:

  Major features:
    * Vk.com support
    * Seafile support (server >= 4.4.1)
    * Add Ampache compatibility (through Subsonic service)
    * Add new analyzer "Rainbow Dash"
    * Answer to the ultimate question of life, the universe and everything
    * Add "Psychedelic Colour" mode to all analyzers

  Other features:
    * Add left click to fullsize cover on playing widget.
    * Add m4b support for non-drm files.
    * Ignore English articles for library sorting.
    * Improve the organize dialog.
    * Add an option to warn before closing a playlist tab.
    * Add an option to disable the pause notification.
    * Add options to hide some internet services.
    * Add an option to disable inline song metadata editing.
    * Add "details below" and "no details" now playing widget options.
    * Add "no song details" now playing widget option.
    * Add icons to the extras menu.
    * Add a source icon for CD tracks.
    * Allow user to remove directories in the Files tab.
    * Add ability to remove unavailable items from playlist.
    * Add a button to the transcode dialog to add all files in a directory.
    * Make it impossible to collapse either side of the MainWindow splitter.
    * Add menu items for updating and doing a full rescan of Google Drive.
    * Increase Soundcloud cover image size.
    * Add the ability to pause Spotify tracks.
    * Add the ability to add or remove a Spotify track to a Spotify playlist
      through context menu.
    * Add Spotify tracks to Spotify playlists by drag and drop.
    * Add ability to get a link to share Spotify playlists and songs.
    * Improve handling of Spotify Top Tracks and compilations.
    * Add playlist actions to Spotify songs.
    * Add ability to automatically set podcast as listened after successfully
      sending it to a device.
    * Add ability to order podcasts by age.
    * Allow user to download multiple podcasts at the same time.
    * Add ability to cancel podcast downloads in progress.
    * Allow user to hide listened podcast episodes.
    * Huge improvement of the speed at startup.
    * Improve performance of mass rating changes.
    * Improve ripping performance.
    * Persistent cache for pixmaps. Huge improvement of the performance when
      scrolling the library for example.
    * Add AppData file for Clementine (for GNOME and KDE Software Centers).
    * Add iPod-like behaviour to previous button.
    * Add HipHop and Kuduro equalizers.
    * Remember current playlist between restarts.
    * IDv3 tag lyrics support.
    * Scroll to last played track when switching playlists.
    * Add stop after each song repeat mode.
    * Sort discs numerically when using Group by disc.
    * Add ability for sort by group and performer in the library view.
    * Parse the year of a disc from musicbrainz.
    * Add track intro mode.
    * Add ability to add a search term with tab and space in the smart playlist
      window.
    * Add love/ban (Last.fm) global shortcuts.
    * Add support for "original year" tags.
    * Send album artist to Last.fm with liblastfm >= 1.0.0.
    * Add sample rate selection.
    * Add option to change the time step when seeking using the keyboard.
    * Playlist sort by album considers disc and track numbers.
    * Add options for double clicking song in the playlist.
    * Volume slider handles glow effect using system theme.
    * Library view sort line themable.
    * Show track durations in the CD ripper dialog.
    * Add ability to read REM DISC tag from Cue sheet.
    * Add ability to lock/unlock rating edit status.
    * Add the support of trackNum elements in XSPF.
    * Add support for inhibiting the screensaver on windows.
    * Add "Smart Playlists" for Subsonic.
    * Add lyrics from AZLyrics.
    * Add lyrics from bollywoodlyrics.com.
    * Add lyrics from hindilyrics.net.
    * Add lyrics from lololyrics.com.
    * Add lyrics from Musixmatch.
    * Add lyrics from Tekstowo.pl.
    * (Mac OS X) Use Alt+Tab to switch between playlist tabs.

  Bugfixes:
    * Fix crash when click on a SoundCloud entry in internet tab.
    * Fix crash when marking podcast as listened.
    * Fix crash after pressing OK in the device properties window.
    * Fix stop after track which doesn't remove now playing.
    * Fix play bleeding into next track after auto stop.
    * Fix analyzer framerate when mouseover play scrubber.
    * Fix issues with buffers sent to analyzer.
    * Fix block analyzer framerate.
    * Fix divide-by-zero possibility with small buffers at end of track.
    * Fix divide-by-zero possibility in moodbar.
    * Fix oversized album cover art.
    * Clean cover art from /tmp.
    * Fix the rendering of the little numbers in the boxes on queued items in
      the playlist.
    * Fix parsing of MusicBrainz data for discid.
    * Fix random artifacting on nyanalyzer on startup.
    * Fix podcasts length issues (which caused issues with seeking for example).
    * Fix too small equalizer window size.
    * Fix labels which don't inherit system text colors in the edit tag dialog.
    * Fix the mess of the queue manager after playlist re-sort.
    * Fix for queue ordering issue in the playlist view when using Ctrl+D to
      dequeue a track.
    * Fix detection of parent-relative paths in playlist saving.
    * Fix path seperators issue when reading playlists.
    * Fix m3u parser issue when an artist's name has a hyphen.
    * Fix bug with percents when fetch the Jamendo catalogue.
    * Fix a little dropout when transition to next track.
    * Fix broken RockRadio.com for premium users.
    * Fix Subsonic login with + characters in the password.
    * Fix accents issue in when save playlist in xspf format.
    * Fix issues with some songs length thanks to Taglib. People with Taglib
      installed on their system will have to wait a new release of Taglib.
    * Fix moodbars not generating correctly.
    * Fix socket leak in moodbar.
    * Fix memory leak in tagreader.
    * Fix crash when trying to fingerprint but missing a plugin.
    * Fix infinite scan with Subsonic when the library is empty.
    * Fix shortcut/media keys issues on Mac.
    * Fix compilation issues on Yosemite.
    * Fix performer tag for mpeg.
    * Fix parsing issues with "innovative" datetime formats.
    * Fix laggy interface on Mac.
    * Fix playback breaks in Spotify.
    * Fix memory leaks.
    * Fix crash when stopping song that is fading after pausing.
    * Fix crash when trying to download a track but there is no current one
      playing.
    * Fix default spinner gif image which shows white pixels around the image.
    * Fix setting album artist tag for FLAC files if it already exists.
    * Fix crash when Clementine lists the albums on Ampache.
    * Fix Last.fm scrobbling after seek.
    * Fix metadata not processed properly for some streams (Akamai).
    * Fix save state when the song was paused.
    * Fix some issues in Boom and Turbine analyzers.
    * Fix song continuously rewinding when seeking using keyboard arrow keys.
    * Fix OSD re-posistioning which doesn't work on multiple monitors.
    * Fix Sonogram state while paused.
    * Fix crash when changing 'group by' while album covers are still loading.
    * Fix loss of valid data from an mp3 file when using the metadata editor.
    * Fix track slider twitching.
    * Fix Di.fm stations stuck when try to play them without internet.
    * Make mood files hidden in NTFS.
    * Fix time labels blinking when playing streams without known duration.
    * Fix tag fetcher which applies incorrect tags for songs without any results.
    * Fix Clementine getting stuck when transitioning from a local track to a
      Spotify track with crossfade disabled.
    * Fix previous track when playing a dynamic random mix.
    * Fix fullscreen album covers for monitors in portrait mode.
    * Don't scale down star icons by 1 pixel.
    * (Mac OS X) Fix Soundcloud API Search which simply doesn't work
    * (Windows) Fix context menu for the "now playing widget"

  Removed features:
    * Remove Ubuntu One support.
    * Remove Discogs support.
    * Remove GrooveShark support.
    * Remove Radio GFM support.

  Build system changes:
    * Update to gstreamer 1.0.
    * Don't compile vreen with link-time optimizations.
    * Use the system's sha2 library if it's available.
    * Remove libindicate-qt.
    * Remove internal copy of libechonest and add it as dependency.
    * Use libcrypto++ instead of QCA.
    * Update TagLib to 1.10.0.
    * (Windows) Uninstall a previous install of Clementine when installing a new
      version.
    * (Windows) Remember the last installation path.
    * (Windows) Add libgmp-10.dll which is required by libgiognutls.dll.
    * (Mac OS X) Use a GTlsDatabase for gstreamer SSL.
    * (Linux) Follow freedesktop.org specifications for icons.
    * (Linux) Add a 128x128 version of the Clementine icon.
    * (Debian/Ubuntu) Remove internal copy of chromaprint and add it as
      dependency.
    * (Debian/Ubuntu) Add libmygpo-qt-dev (=> 1.0.7).
    * (Fedora) Don't depend on libplist or usbmuxd."

```

---

### Post by Rocky_Bennett on 2016-04-16
Unfortunately Clementine is one of the worse sounding music player apps around. I can not listen to it for more than about one minute before my ears start hurting. It just processes the data stream too much which makes it an unenjoyable experience.

---

### Post by night_sky2 on 2016-04-16
I use Banshee Media Player. It's the only one that works flawlessly with my Samsung Mp3 Player.

---

### Post by Giel_D on 2016-04-17
> **Rocky_Bennett said:**
> Unfortunately Clementine is one of the worse sounding music player apps around. I can not listen to it for more than about one minute before my ears start hurting. It just processes the data stream too much which makes it an unenjoyable experience.

I cannot fathom how Clementine could be hurting your ears. Why would its sound be different than any other music application? I'm very interested in hearing your answer.

---

