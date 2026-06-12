---
title: "Scripting windows registry offline editing! (Updated)"
date: 2018-06-06
forum: Tutorials
---

### Post by Shrout1 on 2018-06-06
I've spent most of today figuring out how to use chntpw to modify an offline windows registry non-interactively. There is an [*ancient* tutorial here]("https://ubuntuforums.org/showthread.php?t=1131723") that doesn't seem to work anymore, but it got me on the right track.

The key to making chntpw function non-interactively is a "Here document" or a section of a bash script that can pass successive commands, interactively, into a tool. The section of the script then closes the interactive tool, thus completing its task without requiring user interaction. Here is an updated version of the 10 year old tutorial.

The following example code will execute chntpw interactively, move it into the specified location in the hive, ls out the values within and then quit:

```

#!/bin/bash
#REMEMBER TO SUDO ME!
ntfs-3g /dev/sda2 /mnt/sda2
cd /mnt/sda2/Windows/System32/config
#Run the following 'Here Document' for all commands between CommandsIndicatorString
chntpw -e SOFTWARE<<- CommandsIndicatorString
	cd Microsoft\Windows NT
	ls	
	q
CommandsIndicatorString
```

A few things of note:

[LIST]
[*]**<<- CommandsIndicatorString** is the beginning of the command sequence, with "CommandsIndicatorString" being the "limiter" string
[*]The 2nd use of the "limiter" ("CommandsIndicatorString") will cause the command sequence to stop and the bash script will resume normal execution, away from the STDIN of the binary specified at the start of the command (in this case it will stop feeding commands into chntpw).
[*]It's best to use a unique limiter string.
[*]The **"-"** added after the **"<<"** (I.E. **"<<-"**") allows the text after the first line in the "Here Document" section to be tab indented. The bash script will then ignore the tabs in this space (this is for formatting purposes only).
[*]Also note that all commands must be entered just as they would be typed on the keyboard.
[/LIST]

Here is a quick guide to some of the chntpw command flag options [(from here)]("https://github.com/rescatux/chntpw/blob/master/regedit.txt"):
[LIST]
[*]hive [<n>] - list loaded hives or switch to hive numer n'
[*]cd <key> - change key
[*]ls | dir [<key>] - show subkeys & values,
[*]cat | type <value> - show key value
[*]st [<hexaddr>] - show struct info
[*]nk <keyname> - add key
[*]dk <keyname> - delete key (must be empty. recursion not supported yet)
[*]ed <value>            - Edit value
[*]nv <type> <valuename> - Add value
[*]dv <valuename>        - Delete value
[*]delallv               - Delete all values in current key
[*]debug - enter buffer hexeditor
[*]q - quit
[/LIST]

for nv <type> <valuename> (adding a value to a key) the list of <types> from chntpw is as follows:

[LIST=1]
[*]REG_SZ
[*]REG_EXPAND_SZ
[*]REG_BINARY
[*]REG_DWORD
[*]REG_DWORD_BIG_ENDIAN
[*]REG_LINK
[*]REG_MULTI_SZ
[*]REG_RESOURCE_LIST
[*]REG_FULL_RES_DESC
[*]a = REG_RES_REQ (use lowercase 'a' as the type)
[*]b = REG_QWORD (use lowercase 'b' as the type)
[/LIST]

**USE THE TOOL MANUALLY BEFORE TRYING TO SCRIPT ANYTHING!** It's very important to test all your commands and your syntax before trying to script it. Be sure to back up / export the target registry hive before modifying so that there is a clean copy on hand in case of disaster.

Hope this helps someone else fight the good fight!

---

