---
title: "[SOLVED]I can't install Anydesk on Ubuntu server"
date: 2021-03-30
forum: Server Platforms
---

### Post by ghezzi-alex on 2021-03-30
[COLOR=#101010][FONT=Ubuntu]Good evening everybody[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]I'm trying to install anydesk on ubuntu server i'm already running on an old PC, but I've found some difficulties.
I'll try to brief what I'm doing so you can tell me what i'm doing wrong:
[/FONT][/COLOR]After I had installed [COLOR=#101010][FONT=Ubuntu]UBUNTU server 20.10 (64bit) and install over it the graphic interface tasksel, I downloaded the [/FONT][/COLOR][COLOR=#101010][FONT=Ubuntu]Debian/Ubuntu/Mint 64bit from the official anydesk italian site.[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]Once dowloaded starting from the directory I gave this command:[/FONT][/COLOR]
**sudo dpkg -i anydesk*. deb**

[COLOR=#101010][FONT=Ubuntu]This is what it gave me back:[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]"(Reading database ... 124520 files and directories currently installed.)[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]Preparing to unpack anydesk_6.1.0-1_amd64.deb ...[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]Failed to stop anydesk.service: Unit anydesk.service not loaded.[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]Unpacking anydesk (6.1.0) over (6.1.0) ...[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]dpkg: dependency problems prevent configuration of anydesk:[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]anydesk depends on libgtkglext1; however:[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]Package libgtkglext1 is not installed.[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]dpkg: error processing package anydesk (--install):[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]dependency problems - leaving unconfigured[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]Processing triggers for hicolor-icon-theme (0.17-2) ...[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]Processing triggers for desktop-file-utils (0.24-1ubuntu4) ...[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]Processing triggers for mime-support (3.64ubuntu1) ...[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]Errors were encountered while processing:[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]anydesk"[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]Are you able to understand where I'm doing wrong?
I tried also to give this command: [/FONT][/COLOR][COLOR=#005400][FONT=Monaco]sudo apt install libgtkglext1.
[/FONT][/COLOR][COLOR=#101010][FONT=Ubuntu]Installing this library It gave me back an error as well. 
[/FONT][/COLOR]I hope to have given to you all the elements to understand what's going on.
thanks in advance to everybody
[COLOR=#101010][FONT=Ubuntu]Alex[/FONT][/COLOR]

---

### Post by mikewhatever on 2021-03-30
Well, it needs some dependencies, so run <sudo apt-get install -f> to install them.

---

### Post by scorp123 on 2021-03-30
As Mike above has already said:

```
sudo apt-get -f install
```

Also: AnyDesk doesn't work too well with Wayland. Consider turning it off.
[https://support.anydesk.com/AnyDesk_on_Linux]("https://support.anydesk.com/AnyDesk_on_Linux")
[https://askubuntu.com/questions/1131921/anydesk-remote-server-display-not-supported-e-g-wayland]("https://askubuntu.com/questions/1131921/anydesk-remote-server-display-not-supported-e-g-wayland")

---

### Post by ghezzi-alex on 2021-03-31
Got it!
Thanks a lot everybody

---

