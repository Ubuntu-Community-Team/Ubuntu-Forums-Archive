---
title: "Repository/update help? can't seem to get it to work"
date: 2005-05-01
forum: Repositories &amp; Backports
---

### Post by agentworm on 2005-05-01
I've been trying to update my Ubuntu through the System->add/remove->advanced method, but it keeps giving me an error. So I have tried going through the terminal doing:

sudo apt-get update

Both methods give me this error:

W: Couldn't stat source package list [ftp://neacm.fe.up.pt](ftp://neacm.fe.up.pt) binary/ Packages (/var/lib/apt/lists/neacm.fe.up.pt_pub_ubuntu-java_binary_Packages) - stat (2 No such file or directory)

or time out at this address:

Err [ftp://neacm.fe.up.pt](ftp://neacm.fe.up.pt) binary/ Packages
  Could not connect to neacm.fe.up.pt:21 (193.136.28.167), connection timed out


I will completely honest with you guys. I'm very new to this stuff. I had installed Ubuntu about 2 or 3 months ago, but got a bit frustrated (XMMS or whatever the music player is called wasn't working, and I STILL can't get the java firefox plugins to work, not to mention my videocard driver installation STILL eludes me  :| ). Some friends suggested I do some changes but I don't remember what exactly they were. If anyone has any suggestion as to how to fix (or change) that connection problem, please let me know.

Thank you for your time.

---

### Post by agentworm on 2005-05-01
[QUOTE=agentworm]I've been trying to update my Ubuntu through the System->add/remove->advanced method, but it keeps giving me an error. So I have tried going through the terminal doing:

sudo apt-get update

Both methods give me this error:

W: Couldn't stat source package list [ftp://neacm.fe.up.pt](ftp://neacm.fe.up.pt) binary/ Packages (/var/lib/apt/lists/neacm.fe.up.pt_pub_ubuntu-java_binary_Packages) - stat (2 No such file or directory)

or time out at this address:

Err [ftp://neacm.fe.up.pt](ftp://neacm.fe.up.pt) binary/ Packages
  Could not connect to neacm.fe.up.pt:21 (193.136.28.167), connection timed out


I will completely honest with you guys. I'm very new to this stuff. I had installed Ubuntu about 2 or 3 months ago, but got a bit frustrated (XMMS or whatever the music player is called wasn't working, and I STILL can't get the java firefox plugins to work, not to mention my videocard driver installation STILL eludes me  :| ). Some friends suggested I do some changes but I don't remember what exactly they were. If anyone has any suggestion as to how to fix (or change) that connection problem, please let me know.

Thank you for your time.[/QUOTE]
 n/m on this error...I just removed that repository from my list... things seem okay...for now... o_O

---

### Post by Zensunni on 2005-05-01
How did you fix it exactly? I'm having the same problem...(i don't even know what a repository is....)

---

### Post by agentworm on 2005-05-01
[QUOTE=Zensunni]How did you fix it exactly? I'm having the same problem...(i don't even know what a repository is....)[/QUOTE]
 I went into the Add/Remove Programs Advanced section, then into repositories and removed two of the repositories that were in there. I believe I had added those some time ago to try and get the java plugin working with firefox.

---

