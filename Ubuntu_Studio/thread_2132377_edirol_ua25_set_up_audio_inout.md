---
title: "edirol ua25 set up audio in/out"
date: 2013-04-04
forum: Ubuntu Studio
---

### Post by lamblamb1982 on 2013-04-04
Hello,
i'm trying to set up **edirol UA25** to play guitar** with Rakarrack** on ubuntu 12.04
in the set up window of qjackctrl I selected (I think so) the correct options: i've seen a correct one in the forum
in the audio set up of linux I choose UA25 for in and out

but

in the connection window of Qjackctrl I **can't see UA25**, but only system and rakarack for in and out
in the system input ther are two mycrophone icons

the problem is that rackarack captures the audio, **[COLOR=#ff0000]not from edirol[/COLOR]** in, **[COLOR=#ff0000]but from pc mic[/COLOR]**.
and the same is for the output., it comes from pc speaker.

I tryed to change usb port to connect edirol, but nothing changed

any idea?
thanks

---

### Post by jejeman on 2013-04-04
Give
```
aplay -l
```You didn't select right card for JACK. It will always be "system" in qjackctl, thats just how JACK names audio ports from soundcards.

---

### Post by zequence on 2013-04-04
Before starting jack, make sure to choose the correct device. You do this from: Qjackctl -> Setup -> Interface.

---

### Post by lamblamb1982 on 2013-04-04
aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: ALC262 Analog [ALC262 Analog]
  Sottoperiferiche: 0/1
  Sottoperiferica #0: subdevice #0
scheda 1: UA25 [EDIROL UA-25], dispositivo 0: USB Audio [USB Audio]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
carlo@reginald:~$ 

[B]ok, thanks
[/B]
it gives me that 

I don't understand what does it mean that I have to choose the right audio device **before** starting jack
Sorry but I'm a beginner with audio software in linux

In set up of qjackctrl I choose my audio hardware Edirol UA25
than, what do i have to do?

I used qjackctrl to set up connection. is it right?

---

### Post by lamblamb1982 on 2013-04-04
this is my set up 
hw:1 is my hardware

---

### Post by zequence on 2013-04-04
By choosing the right audio device, I meant choosing the right audio card, in your case the Edirol UA25.

Once you have chosen the correct device, just start jack.

---

### Post by zequence on 2013-04-04
Here is some general info on Ubuntu Studio audio [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro)

---

### Post by jejeman on 2013-04-04
> **lamblamb1982 said:**
> this is my set up 
hw:1 is my hardware
Yes, hw1 should be your device. No need to define input device, leave it on default. Just choose interface.

---

### Post by zequence on 2013-04-04
Ah, yes. I missed this. Do not set input and output separately - set those to "default". 
Just use "interface" for choosing your card.

---

### Post by lamblamb1982 on 2013-04-04
ok, I've just tryed , choosing my audio card and than starting jack.

I've read the the passes to start jack on the link

but starting jack it gave me that message:

Cannot connect to server socket err = File o directory non esistente
Cannot connect to server socket
jack server is not running or cannot be started
QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0xbfb26ac0) "" 
FIXME: handle dialog start. 
Thu Apr  4 23:49:18 2013: Starting jack server...
Thu Apr  4 23:49:18 2013: JACK server starting in non-realtime mode
Thu Apr  4 23:49:18 2013: [1m[31mERROR: Cannot lock down 82241434 byte memory area (Cannot allocate memory)[0m
Thu Apr  4 23:49:18 2013: control device hw:1
Thu Apr  4 23:49:18 2013: control device hw:1
Thu Apr  4 23:49:18 2013: [1m[31mERROR: Failed to acquire device name : Audio1 error : Cannot allocate memory[0m
Thu Apr  4 23:49:18 2013: [1m[31mERROR: Audio device hw:1 cannot be acquired...[0m
Thu Apr  4 23:49:18 2013: [1m[31mERROR: Cannot initialize driver[0m
Thu Apr  4 23:49:18 2013: [1m[31mERROR: JackServer::Open() failed with -1[0m
Thu Apr  4 23:49:18 2013: [1m[31mERROR: Failed to open server[0m
FIXME: handle dialog end. 
[COLOR=#ff0000]23:49:20.463 Non sono riuscito ad avviare JACK come client. - Operazione fallita. - Impossibile connettersi al server JACK. Controlla la finestra dei messaggi per maggiori informazioni.[/COLOR]
Cannot connect to server socket err = File o directory non esistente
Cannot connect to server socket
jack server is not running or cannot be started
QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0xbfb27330) "" 
FIXME: handle dialog start. 
Thu Apr  4 23:49:20 2013: Saving settings to "/home/carlo/.config/jack/conf.xml" ...
FIXME: handle dialog end. 
QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0xaa338c8) "" 

thank you for your time!

---

### Post by zequence on 2013-04-04
This means you don't have realtime privilege, and that also means you are not on Ubuntu Studio ;)
> Thu Apr  4 23:49:18 2013: JACK server starting in non-realtime mode

This means you don't have the athority to lockdown memory.
> Thu Apr  4 23:49:18 2013: [1m[31mERROR: Cannot lock down 82241434 byte memory area (Cannot allocate memory)[0m

That shouldn't stop you from being able to start jack though. But, before you go further, you might as well make sure you have things set up right.

rtprio and memlock are set up in this file, granting users who are members of audio group access to them.
```
/etc/security/limits.d/audio.conf
```

If you didn't say yes to realtime during installation of jackd, the file will be named /etc/security/limits.d/audio.conf.disabled. Rename it to the former. You can start your file browser as admin with the command:
```
gksudo <filebrowser>
```
Replace <filebrowser> with either **nautilus** or **thunar**, depending on which one you have installed.

The file should look like this when you open it:
```

# Provided by the jackd package.
#
# Changes to this file will be preserved.
#
# If you want to enable/disable realtime permissions, run
#
#    dpkg-reconfigure -p high jackd

@audio   -  rtprio     95
@audio   -  memlock    unlimited
#@audio   -  nice      -19

```

In order to become member of audio group, in a terminal, do:
```
sudo usermod -a -G audio $USER
```

You'll need to reboot in order for changes to take effect.

Then, to troubleshoot, I would read this first: [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro#UbuntuStudio.2BAC8-ProAudioIntro.2BAC8-1204.USB_troubleshooting](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro#UbuntuStudio.2BAC8-ProAudioIntro.2BAC8-1204.USB_troubleshooting)

---

### Post by zequence on 2013-04-04
Your device seems to be well supported, so it should not be too hard to get it started in full duplex. You can read more about that here [http://wiki.linuxmusicians.com/doku.php?id=edirol_ua-25ex](http://wiki.linuxmusicians.com/doku.php?id=edirol_ua-25ex)

---

### Post by lamblamb1982 on 2013-04-05
ok
i succeed in renaming the directory audio.conf.disabled and turned it in audio.conf
the code was gksudo "nautilus" with "" and not <>! i don't know why.

and then appeared a graphic acces to my home directory like admin, not from the terminal: better for me!

as soon as possible i will try to set up qjackctrl and see if i will find my audio device

thank you!

---

### Post by lamblamb1982 on 2013-04-05
[COLOR=#ff0000]17:09:43.845 Non sono riuscito ad avviare JACK come client. - Operazione fallita. - Impossibile connettersi al server JACK. Controlla la finestra dei messaggi per maggiori informazioni.[/COLOR]
Cannot connect to server socket err = File o directory non esistente
Cannot connect to server socket
jack server is not running or cannot be started
QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0xbff8d8f0) "" 
FIXME: handle dialog start. 
Fri Apr  5 17:09:43 2013: Saving settings to "/home/carlo/.config/jack/conf.xml" ...
FIXME: handle dialog end. 
QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0xae04b30) "" 

so, it is the same 

in paychbay i can see my device like alsa

the message says (the part in italian) [COLOR=#ff0000]can't run jack as client. it is not possible to connect at jack server[/COLOR]

---

### Post by lamblamb1982 on 2013-04-05
could it be a problem of jack version?
i have 1.9.6
now i'm trying install 1.9.9 ( jack2 ?)

---

### Post by zequence on 2013-04-05
<> is common for saying it is a variable, which you should replace, so not meant to be used in the command. So, you were right.

The jack version should make no difference. I don't know about Ubuntu Studio version though. It would have more to do with the kernel version actually, most probably. As the device requires a special drivers that is found in the kernel. But, could be the drivers has been included for a long time already.

No, I think it has more to do with configuration. are you able to start jack with your other audio device?

---

### Post by zequence on 2013-04-05
I don't know which device is your USB device, but let's assume it is hw:1.
To find out you can either look in qjackctl, or do this command:

```
cat /proc/asound/cards
```

The number tells you which it is.

Now, to start jack, you could do these commands in series.

First, make sure jackdbus and jackd are killed:

```
killall -9 jackdbus
killall -9 jackd
```

Then, assuming your USB device is hw:1, start jack abd  suspending pulseaudio at the same time:
```
pasuspender -- jackd -d alsa -d hw:1
```

suspending pulseaudio was done with the command "pasuspender --"

You can also just start jack with:
```
jackd -d alsa -d hw:1
```

---

### Post by lamblamb1982 on 2013-04-05
ok, after i gave the command from terminal jack started with theese option
there are the attachments of screenshot of
patchbay, that i have not understand what is, yet

connection option for audio and alsa. in midi, no option
in audio there is not my audio device
you can see it in alsa window, but it is midi in/out, not audio

---

### Post by lamblamb1982 on 2013-04-05
and i had no answer to the code that was supposed to find out if jack was killed
it told me directory not found or similar message

---

### Post by zequence on 2013-04-06
It looks like you were able to start your USB device, so that is good news.

Let me explain the different tabs that you took pictures of:

Audio is as you might expect, connectivity for audio in and out. When you open jack applications, such as Hydrogen, you can connect their audio ins and outs to your USB device, which is marked as "system".
Midi is only for jack midi connections.
ALSA is only for ALSA midi connections.

When you do the "killall" command, if you get no return at all, that means you successfully killed a process with that name. 
If you get "no process found", it simply means, there was no such process active.
I just wanted to make sure the processes were killed first.

There is a bug in jackdbus (which should get fixed very soon - [https://bugs.launchpad.net/ubuntu/+source/jackd2/+bug/956438](https://bugs.launchpad.net/ubuntu/+source/jackd2/+bug/956438)), that when you try to stop it, it crashes. when this happens, you always need to kill it, before starting it again, with the command:
```
killall -9 jackdbus
```

When you use qjackctl to start jack, the default option is to start jackdbus, not jackd. When you started jack from the terminal the way I showed you, you started jackd. They are the same program, but they work differently.

---

### Post by lamblamb1982 on 2013-04-06
[I][COLOR=#000000]Audio is as you might expect, connectivity for audio in and out. When you open jack applications, such as Hydrogen, you can connect their audio ins and outs to your USB device, which is marked as "system".[/COLOR]
[COLOR=#000000]Midi is only for jack midi connections.[/COLOR]
[/I][COLOR=#000000][I]ALSA is only for ALSA midi connections.
[/I]

ok! 
what i don't understand is why i can't see **alsa audio in audio section**. (right?)
or the mistake is that since i abilited UA25 as my USB device, it became my system in place of my internal pc system? ( if not it means that i haven't understand what usb device is supposed to do:[/COLOR][COLOR=#ff0000] it is hw:n,[/COLOR][COLOR=#000000] right?)
i thought i could see[/COLOR][COLOR=#ff0000] **ALSA in/out or UA25 in/out in AUDIO section**[/COLOR][COLOR=#000000]**.** i say that because connecting rackarrack to system, it use my pc mic and my pc speaker as in and out.
not  jack audio in and out of my external audio card

am I wrong with something?[/COLOR]

---

### Post by jejeman on 2013-04-06
As I said in post #2
>  It will always be "system" in qjackctl, thats just how JACK names audio ports from soundcards. You will never see soundcard name it will always be "system" regardles it is PCI, USB or firewire audio card.
You need to understand this
[http://tuxradar.com/content/how-it-works-linux-audio-explained](http://tuxradar.com/content/how-it-works-linux-audio-explained)

It should not matter, but, you can try to set in pulseaudio input card to be UA25, and see if there is any difference.

---

### Post by zequence on 2013-04-06
All audio cards are as said usually always named "system" in qjackctl. 
If you see "system", that means jack is running with the device you chose. Otherwise, that view would just be empty.
You will never see audio devices in the Audio view, that you didn't choose in qjackctl setup.

---

### Post by lamblamb1982 on 2013-04-06
ok..this is because i saw this image, wich is also in the link you posted me. 
alsa appears in place of system. it means that it is only renamed, otherwis it was system?

---

### Post by lamblamb1982 on 2013-04-06
sorry! i missed the image

---

### Post by lamblamb1982 on 2013-04-06
and now he said that my device can not be found..here the terminal screenshot

---

### Post by zequence on 2013-04-06
> **lamblamb1982 said:**
> and now he said that my device can not be found..here the terminal screenshot

This error "cannot be acquired" is most likely due to pulseaudio using your card, when you are trying to start jack. This is a bug, which is fixed in Ubuntu Studio 13.04, and will be fixed for 12.04 and 12.10 soon.

For best result, make sure pulseaudio is not using the card you want to use with jack.

---

### Post by jejeman on 2013-04-06
> **lamblamb1982 said:**
> ok..this is because i saw this image, wich is also in the link you posted me. 
alsa appears in place of system. it means that it is only renamed, otherwis it was system?
Okay,
In the end, I guess, it all depends on the configuration. For Ubuntu Studio it was and it is always "system".

---

