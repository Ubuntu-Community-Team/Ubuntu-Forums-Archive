---
title: "Kile 1.9.2 for Dapper - .deb available"
date: 2006-09-10
forum: The Cafe
---

### Post by luca.b on 2006-09-10
I'm not sure this is the right section, but I'll give it a go here first. Moderators, feel free to move or delete my post if needed.
Last month there was a new release of tke Kile LaTeX environment (1.9.2), mainly a bugfix release. As there's no package for dapper yet, I decided to build one, and now I want to make it available for everyone. To give credit where it's due, I used the debianized source already available on the repository and rebuilt it for the new version (so big thanks to the original packagers).

**Disclaimer:** Originally I built this for myself. It should work in most situations, but I make no claims. Use the package at your own risk.

The links have expired. See below in the thread for links.

The package has been digitally signed with my GPG key, available on the wwwkeys.pgp.net keyserver (key ID EC445369) or on [my own web page]("http://www.dennogumi.org/lb.key").

Changes:
version 1.9.1 -> 1.9.2
Fixes:
 - Add autoref command to standard reference commands (#130037)
 - Remember the setting of MakeIndexOptions checkbox in the project settings
 dialog. (debian #337550)
 - Added utf-8 and other encodings to the quickdocument dialog. (#131402)  
 - Make the "New Tool" dialog box big enough. (#132425)
 - Check if masterdocs in kilepr files exist, should fix some problems with upgrades from kile 1.8.
 - Searching for environments in Edit functions improved.
 - Take array as math environment instead of tabular in Configure->Latex Environments.
 - Don't crash if a user changes the icon of a toolbar item. (debian #382317)
 - Allow a few more punctuation in codecompletion of citation keys. (#130148)
 - Remember last working directory in 'find in files' dialog. (debian #359932)
 - Tabular wizard should insert all entered elements. (#132736)
 - Only autosave files which have been modified.
 - Delete comma of last bibtex entry if Bibliographie->Clean is called. (#129499)
 - Quick Preview fails if graphics are included in selection (#126019)

---

### Post by lodp on 2006-10-18
hm.. the download link has expired -- would you mind re-uploading this somewhere else?

---

### Post by luca.b on 2006-10-18
Will do, please poke me around the weekend so I don't forget (I'm quite busy lately).

---

### Post by luca.b on 2006-10-23
Ok, I updated the links. Hop to [my blog page](http://www.dennogumi.org/2006/09/10/kile-192-for-kubuntu-dapper/) to find them (not posting direct links as this is a high-traffic web page).

---

