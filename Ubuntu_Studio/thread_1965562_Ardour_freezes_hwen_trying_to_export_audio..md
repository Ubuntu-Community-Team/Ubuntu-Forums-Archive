---
title: "Ardour freezes hwen trying to export audio."
date: 2012-04-26
forum: Ubuntu Studio
---

### Post by benqu on 2012-04-26
Hello. 

I made recording whit Ardour wia Qjack and Guitarix. I made connections in Qjack like in this page: [http://epenguin.imalone.co.uk/2011/12/re-amping-with-guitarix-and-ardour.html](http://epenguin.imalone.co.uk/2011/12/re-amping-with-guitarix-and-ardour.html) 

But when I was going to export audio Ardour froze. I tryed many times, but always it froze. I had to kill Ardour process and after restarting Qjack i had no sound anymore. Broblem could be in QJack

I have ubuntu_studio 12.04 
My soundcard is M-audio fast track pro M-audio fast track pro. 

Other problem is that my system doesen't find m-audio always. I have to restart fast track pro or the computer. Sometimes i have to do both and still it doesen't work and sometimes system finds it at start.

Help me if you can.



if you want more information i can tell..

---

### Post by Fincer on 2012-04-26
Hey,

so you can record audio but not save it. Though I don't know Ardour exactly in detail, it seems that you'd better start solving the problem by typing following sentences in your terminal.

First we need to be sure what version of kernel you use in Ubuntu Studio 12.04 LTS. To find it out, type

```
uname -r
``` (or alternatively *uname -a*)

secondly, I recommend that you run the program through terminal. Simply open the terminal and type the program name (ardour, perhaps?). You may see several warning messages on the first look but ignore them. The one we are interested in is the message that is printed out in terminal at the moment when Ardour actually crashes.

The fore mentioned command may not be the one which opens the program every time you click Ardour's desktop icon. These commands may vary from program to program... so, if you wish to see the exact command that opens Ardour, check

1) the information inside Ardour desktop shortcut file (*/home/<user_name>/.local/share/applications/*). The field we are looking for is called *Exec=*
2) your desktop main menu application configurations (I'm not sure about XFCE environment, sorry)

Personally, I recommend you to grab that exact command because it's the only way to make sure that you repeat same commands when opening Ardour in normal (graphical) way in every day use.

Please, paste the terminal output so we could help you to solve this issue. As I said, we are interested only in any error messages you may see in terminal while executing Ardour and saving/exporting audio data.

---

### Post by benqu on 2012-04-26
Thaks for reply. Here is details:

kernel: 3.2.0-23-lowlatency


opening Ardour i got (at end of the terminals text):
powermate: Opening of powermate failed - Lupa evätty
ardour: [INFO]: Control protocol powermate not usable
ardour: [INFO]: Control surface protocol discovered: "Mackie"
ardour: [INFO]: Control protocol Tranzport not usable
ardour: [INFO]: Control surface protocol discovered: "Generic MIDI"
loading bindings from /etc/ardour2/mnemonic-us.bindings

(ardour-2.8.12:2379): Gtk-WARNING **: EnableTranslation: missing action EnableTranslation
Session writable based on /home/<username>/jejea/
Start export at pos = 0
Everybdy is at 0


And i openen Qjackctl too from terminal and i got warnings too:
~$ qjackctl
Warning: no translation found for 'fi_FI' locale: /usr/share/qt4/translations/qt_fi_FI.qm
Warning: no translation found for 'fi_FI' locale: /usr/share/locale/qjackctl_fi_FI.qm


Hope this helps.

---

### Post by Fincer on 2012-04-26
Thanks for further information.

It may be
1) kernel issue (try older or newer kernels?)
2) problems with powermate permissions (Lupa evätty = Permission denied)
3) problems with Control protocols?

I don't think your issue is related to Qjacktool, according the error messages you provided. They refer more to translation problems which are not usually death penalties to a program.

---

### Post by benqu on 2012-04-27
Hello.

I got exporting work if I use motherboards soundcard when I export audio. I can't export when I'm using M-audio Fast Track Pro.  Now exporting needs more work but I can handle it like this until I will get beter solution.

Benqu

---

### Post by Fincer on 2012-04-29
It's glad to hear you've got it work even somehow at least. I hope this will be fixed soon.

Anyway, I don't think this is going to help you but have you checked */etc/modprobe.d/blacklist.conf* in a case of possibly blocked M-audio Fast Track Pro device, referring to any output stuff?

```
sudo nano /etc/modprobe.d/blacklist.conf
```However, I think your issue is more kernel related and not until further kernel updates it won't be fixed. So, be patient - that's all you can likely do.

---

