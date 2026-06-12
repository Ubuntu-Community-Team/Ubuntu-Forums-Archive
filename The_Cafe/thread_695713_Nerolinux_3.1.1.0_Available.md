---
title: "Nerolinux 3.1.1.0 Available"
date: 2008-02-13
forum: The Cafe
---

### Post by Kosimo on 2008-02-13
You can try it on here:

[http://www.nero.com/eng/downloads-linux3-trial.php](http://www.nero.com/eng/downloads-linux3-trial.php)


The change log is still not available.

---

### Post by Kosimo on 2008-02-13
From CDFREAKS website:

For all of you Linux lovers, the new update of Nero Linux 3 is available here, one day before Valentine's day . We fixed lots (really lots) of problems/bugs/misbehaviour for this release, so this is also an explanation why you have had to wait so long for the next demo version.

We first worked a lot on our GUI, in order to have the full support for the Asus Eee PC screen resolution. As a result, the application adapt all its dialog boxes to the current screen resolution at runtime.
After that, we updated the internal NeroAPI used with Nero Linux. This means improved support for newer drives (BD, HD DVD, S-ATA based...), a brand new ASPI, that deals with HAL for locking/unlocking devices and major improvements with hotplug of devices.
Last but not least, we fixed our Audio CD engine. All the problems that has been reported here are now fully fixed, and all the others that our QA found in the meantime .



Changelog for this version:

New features:

    * Nero Linux now fully supports the Asus Eee PC.
    * Based on NeroAPI version 7.20 for better device handling.
    * Nero Linux has now some command line arguments. You can see the full list by typing nero --help or nero --help-all.
    * There is a manpage for the 'nero' executable.
    * Some MIME types are now registered when installing the application for GNOME, XFCE, and KDE desktops. You will then be able to open every handled files by just clicking on it.
    * The FLAC plugin now handles vorbis tags (artist, title, album...) in both encoder and decoder.
    * The device communication library now supports HAL for locking/unlocking devices and detecting device addition/removal.
    * Hotplug is also working even if the /proc/scsi/scsi file is not present, or HAL not usable.
    * There is no need for an application restart when loading the 'sg' module while Nero Linux is already running. The device list will be correctly updated.
    * When adding a file to the compilation, the access rights of this file are now checked, to ensure that no burn error will occur. This check can also be disabled in the 'Options' dialog box.
    * Some additional checks are done before burning a bootable disc, with a logical drive as source, in order to avoid burn process errors.
    * The user can now control the source drive ejection when copying a disc directly from the 'Compilation Properties' dialog box.
    * The user will be warned as soon as he tries to burn a non-standard disc. For example, the application will display a warning dialog box if you try to write an audio compilation on a non-finalized data disc.
    * A Nero Linux XPM pixmap is now installed in the /usr/share/pixmaps folder
    * The Debian package contains a 'Section' entry.


Feature updates

    * The Audio CD engine has been improved to correctly handle the variable bitrate (VBR) MP3 files. The duration of such a file is now computed regarding each frame of the file.
    * The Hex Editor used to view the raw content of a track has been improved to correctly handle selections.
    * The MP3 plugin now allows files with embedded cover arts and large ID3v2 tags.
    * The OGG/Vorbis encoder does not loose anymore the end of the file.
    * The Wav plugin does not crash anymore with imcomplete files.
    * The 'Follow Symbolic Links' option is now fixed for symlinks to regular files.
    * The sound driver is now properly closed when a errneous file is previewed. This avoids Device or ressource busy error.
    * The 'Internet DB' button of the 'Save Tracks' dialog is only enabled when audio tracks are present inside the list widget.
    * The DVD-Video/miniDVD compilations are now correctly loaded. All the items that should go in the VIDEO_TS folder are inside.
    * All kind of data tracks can now be selected for hexadecimal viewing.
    * The 64bits MP3 plugin does not have an executable stack anymore.


Patches:

    * With audio CD compilations, at the end of a track, you might listen to half a second of a previous track. This is now fixed.
    * Fixed the preview of audio files with non-ASCII characters in the compilation editor.
    * The boot locale setting when creating bootable discs, using the DosBootImage.ima image file is now fully working. It is now correctly setting keyboard layout when booting on ths disc.
    * When the multisession setting of the 'New Compilation' dialog box was set to 'Continue Multisession', a 'Select Track' dialog was poping up when creating a bootable disc. This is now fixed.
    * When a disc does not contain any audio track, no FreeDB query is made at all.
    * The boot source is now correctly updated when you change from 'Logical Drive' to 'Image File' and vice-versa.
    * The 'Destination folder' label was missing in the 'Encode Files' dialog box. It is now placed on the left of the text entry widget.
    * Fixed a refresh problem in the 'Save Tracks' dialog when the encoding process is finished. The dialog does not loose the user customization in the track list anymore.
    * Fixed an invalid CD EXTRA recognition in the 'Disc Info' dialog.
    * When displaying the tracks on a disc in the file browser, a FreeDB lookup is triggered only if the disc contains at least one audio track.
    * When closing the 'Save Tracks' dialog, if a track is currently previewed, the preview player is also stopped.
    * The track number field is now correctly set when ripping an audio track from a CD.
    * Fixed some dialog boxes position and the window icon under IceWM.
    * Fixed a crash when displaying the content of an empty disc in the file browser.
    * Fixed some bad warnings dialog boxes claiming that the /sys directory was not mounted.

---

