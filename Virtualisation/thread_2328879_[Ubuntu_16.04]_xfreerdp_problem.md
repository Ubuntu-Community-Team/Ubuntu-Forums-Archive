---
title: "[Ubuntu 16.04] xfreerdp problem"
date: 2016-06-25
forum: Virtualisation
---

### Post by isidoro4 on 2016-06-25
[COLOR=#212121][FONT=Roboto-Regular]Hi,[/FONT][/COLOR][COLOR=#212121][FONT=Roboto-Regular]I have Windows 7/10 installed in VirtualBox.[/FONT][/COLOR]
[COLOR=#212121][FONT=Roboto-Regular]I use xfreerdp for remote opening of Windows programs.[/FONT][/COLOR]
[COLOR=#212121][FONT=Roboto-Regular]Everything works but not mouse pointer. I can't move windows of programs that I have opened remotely[/FONT][/COLOR]

---

### Post by MAFoElffen on 2016-06-26
Example of a startup command for xfreedp is
```

xfreerdp -u user - g 800x600 --no-nla -f --plugin rdpsnd --data latency:50 -- 192.168.x.x

```
What is the command you are starting xfreerdp with?

What is your system's OS and which version of VirtualBox? 64bit host and guest? Hardware specs? ...Just getting a picture of what is there.

---

### Post by isidoro4 on 2016-06-26
Thanks for reply.
I use latest version of VirtualBox (5.22). I have Windows 7 Ultimate and Windows 10 Enterprise on virtual machine.
The command by terminal is 
```
 [COLOR=#333333][FONT=Consolas]xfreerdp /u:user /d:domain /password /app:"||calc" /v:server [/FONT][/COLOR]
```[COLOR=#333333][FONT=Consolas]
[/FONT][/COLOR]The app Calc opens in Ubuntu. I can use my Keyboard but the mouse doesn't effect on it.

---

### Post by MAFoElffen on 2016-06-26
Your host OS is Ubuntu 16.04, right?

Please retrun to your last post and edit > advanced edit ? Highlight the command posted > then select the "#" icon to enclose that within code tags. An admin forum policy ... but is makes code /and/or commands easier to read, without them being mistakenly misinterpreted or translated by the forum's software...

On your command syntax... It starts with no errors when you do that? Cause in Linux. "/Option_Key_Name" is not the format for options to xfreerdp. For refrence, look at the [Ubuntu Man Page For xfreerdp]("http://manpages.ubuntu.com/manpages/precise/man1/xfreerdp.1.html")  The "/" character is what Windows CmdCLI uses to ID Program Option_Key_Names for argument parameter key/value pairs...

Using that man page, how does what you are trying to do translate to that format?

---

### Post by isidoro4 on 2016-06-26
Ubuntu 16.04 is the main OS. Windows 7/10 are on the VirtualBox.
The command syntax goes with no error and opens the Windows Calculator on Ubuntu's Desktop so I can use keyboard but not the mouse. For example I can't move the Calculator on the desktop or press the number key with the mouse.

---

### Post by MAFoElffen on 2016-06-27
When I get home, I'll install it and try to recreate what you are having problems with. Just to see for myself.

---

### Post by blackdot2 on 2017-01-25
> **isidoro4 said:**
> Ubuntu 16.04 is the main OS. Windows 7/10 are on the VirtualBox.
The command syntax goes with no error and opens the Windows Calculator on Ubuntu's Desktop so I can use keyboard but not the mouse. For example I can't move the Calculator on the desktop or press the number key with the mouse.
I have exactly same problem as you. Did you solved it anyhow?

---

### Post by blasmat on 2017-10-20
I am experiencing the same issue.  Were you ever able to get this working properly?

---

