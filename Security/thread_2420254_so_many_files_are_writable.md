---
title: "so many files are writable"
date: 2019-06-01
forum: Security
---

### Post by Skaperen on 2019-06-01
[SIZE=1]this post is not exactly about security, but it is about system operational safety, and is related to security.  mods, if this is the wrong forum to post this, please move it to the best place.[/SIZE]

i find that Ubuntu and all other Linux distros, BSDs, and other Unix-class systems, leave just about all files writable by root.  at least it's not worse than that.  it has been my practice in my home directories of both root and non-root users to have files with read-only permissions unless there is a specific reason to have them be writable, such as log files.  it has caught me from making disasterous typos a couple times.  as part of this, the script i front-end my editor with temporarily makes files i am editing be writable, unless the file is in a no-edit list (in which case i have to use a different command that i rarely use and needs to be entered with a full path).

i'd like to do this with system files.  i can imagine all the potential problems, even if this were just done in the [FONT=courier new]/usr[/FONT] tree.  package upgrades would likely fail all over the place because replacement files can't be written.  they can, if the writing logic either changes the permissions first (and changes them back, afterwards), or if the process of writing a temporary file first, then moving it into place, is done (with or without a linked backup).

i wonder how many systems around the world have been impacted by little accidents editing command lines involving writing a file and slipping onto the enter key before the edit is complete.  IMHO, there could be a lot fewer if most people followed this "most files be read-only" practice throughout their systems.  having once run systems directly from read-only media (except areas that needed to be writable ... which were initially populated when booting up from that media)  to make them more recoverable (just reboot) in case of intrusion, i made one of my earlier typos on such a system and not overwriting an important file, i realized read-only was better.

i would like to see Ubuntu phase into this practice in the future, mostly so that package upgrading handles it properly (use the "temp and move" method everywhere another method is not needed), allowing me to have files in [FONT=courier new]/usr[/FONT] and [FONT=courier new]/bin[/FONT] and so on, be kept mostly read-only.

i am thinking of a new design using containers.  for each installed version (containers make it easier to have more than one) a specially designated container will keep a writable copy.  package upgrades will be done here.  then a container builder script would make a copy of the designated container for all the other containers, as needed.  the main system would not run most things (maybe some machine-wide monitoring tools).  maybe Ubuntu could go in this direction.

---

