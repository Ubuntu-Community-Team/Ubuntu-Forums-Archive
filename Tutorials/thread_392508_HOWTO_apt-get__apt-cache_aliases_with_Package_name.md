---
title: "HOWTO: apt-get / apt-cache alias:es with Package name Tab Completion in Bash"
date: 2007-03-24
forum: Tutorials
---

### Post by Enselic on 2007-03-24
**[SIZE="3"]Abstract[/SIZE]**

In this little howto I will provide a script that enables the use of bash alias:es for common apt commands, like 'sudo apt-get install', while still keeping that tab completion for package names.

**[SIZE="5"]Introduction/The Problem[/SIZE]**

If you've discovered that the command line interface for the packaging system that Ubuntu uses (APT) is quicker to work with than the GUIs available for it, then you've probably been tempted to add aliases to your ~/.bashrc, e.g.

```

# [...]
# At the end of ~/.bashrc
alias sagi='sudo apt-get install'

```

You probably then also noted that TAB completion didn't work with the alias, and TAB completion is really nice to have at times, for example when hunting lib*:s for use when building software.

**[SIZE="5"]The Solution[/SIZE]**

[LIST=1]
[*]Save ['apt_completion.txt']("http://www.ubuntuforums.org/attachment.php?attachmentid=28175&stc=1&d=1174767541") as 'apt_completion' to your home directory (/home/martin in my case)

[*]Add these lines to the end of ~/.bashrc.
```

# For apt alias:es TAB completion
source ~/apt_completion

```

[*]To activate, either restart the Terminal, or reload ~/.bashrc by issuing the command
```

$ source ~/.bashrc

```
[/LIST]

You can now use common apt-commands with aliases, with TAB completion for package names (in a smart way; sagr will only list installed packages, etc). Supported commands are:

**sudo apt-get install**, aliased by default with **sagi**
**sudo apt-get remove**, aliased by default with **sagr**
**apt-cache show**, aliased by default with **acsh**

The script also aliases

**apt-cache search**, aliased by default with **acs**

because it is very useful to have aliased.

**[SIZE="5"]Customization[/SIZE]**

If you want other aliases, you can manually edit the 'SETUP' portion of apt_completion, which is in the beginning of the file and looks like this:

```

############################################################
########################    SETUP    #######################


# These variables specifies what aliases you want

SUDO_APT_GET_INSTALL_ALIAS=sagi
SUDO_APT_GET_REMOVE_ALIAS=sagr
APT_CACHE_SHOW_ALIAS=acsh
APT_CACHE_SEARCH_ALIAS=acs


########################  END SETUP  #######################
############################################################

```

Simply change e.g. 'sagi' to what you prefer, then save your changes.

**[SIZE="5"]How it works[/SIZE]**

The tab completion feature available when using the full command isn't automatically transfered to an aliased command. This is because of how tab completion works within bash. Whenever TAB is pressed, what bash does is basically to see if completion has been registered with the command that precedes the cursor. To get TAB completion to work with the alias:es, one have to register a function that provides the possible completions for that particular command.

I have based apt_completion, which registers these function with the provided aliases,  on bash_completion (written by Ian Macdonald) that comes with Ubuntu.

**[SIZE="3"]Disclaimer[/SIZE]**

The script is probably improvable, and if you look into it you will note that there are som RPM stuff in it, which I have not tested. I left it there since the original bash_completion on which I based the script on had it, and anyone using an RPM system might find those parts useful. Any pointers on the script are appreciated.

**[SIZE="3"]Tested On[/SIZE]**
This script works on at least Ubuntu 6.10 and 7.04 Beta, but I assume it works on all Ubuntu versions. If you don't get it to work, let me know!

**[SIZE="3"]Uninstallation[/SIZE]**
Remove apt_completion and the lines you added to ~/.bashrc, namely
```

# For apt alias:es TAB completion
source ~/apt_completion

```

---

### Post by kwilliam on 2008-06-08
Thanks! This is nicer than the scripts I'd come up with ([http://ubuntuforums.org/showthread.php?t=525170](http://ubuntuforums.org/showthread.php?t=525170)). I found this after searching on tab completion. Pretty complicated script - thanks for sharing it! I'm happy to have tab completion again. The only thing I changed was the names: I call them appget, appgone, appshow, and appgrep.

---

### Post by RATM_Owns on 2008-06-20
I don't like filling up my home directory, so I renamed the file ".apt" (without the quotes) and changed
```
# For apt alias:es TAB completion
source ~/apt_completion
``` to
```
# For apt alias:es TAB completion
source ~/.apt
```

---

### Post by throwawayaccount123123123 on 2012-04-28
For any other readers who come across this post via google, here's a link to the txt file on pastebin:

[http://pastebin.com/HVYNwCPX](http://pastebin.com/HVYNwCPX)

The URL ends in HVYNwCPX

Ubuntuforums.org requires registration to view attachments, which is total and utter ****.

---

### Post by overdrank on 2012-04-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

