---
title: "Lost unity after upgrading to 15.10"
date: 2015-06-27
forum: Ubuntu Development Version
---

### Post by raphaeldc on 2015-06-27
[COLOR=#111111][FONT=Ubuntu]I guess I need some help here...
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've upgrade to ubuntu 15.10 before the alpha 1 was released. The results was that I was only getting a black screen, only with the pointer icon working and could not manage to make it work. I had to install Mate in order to have a working DE.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]It seems that a package called *unity8* is installed, but it doesn't seem to be the full DE. When I try to reinstall *ubuntu-desktop*, it says that there are held broken packages (dependencies) and cannot install it. If I try to install *ubuntu-desktop-next*, it says the same thing, but with other packages.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This is what I get when I try to install *ubuntu-desktop* (sorry, it's in portuguese but I guess someone can recognize it)
[/FONT][/COLOR]
```
Os pacotes a seguir têm dependências desencontradas:
 ubuntu-desktop : Depende: unity mas não será instalado
                  Recomenda: gnome-bluetooth mas não será instalado
E: Impossível corrigir problemas, você manteve (hold) pacotes quebrados.
```
[COLOR=#111111][FONT=Ubuntu]
This is what I get when I try to install *ubuntu-desktop-next*:
[/FONT][/COLOR]
```
Os pacotes a seguir têm dependências desencontradas:
 ubuntu-desktop-next : Depende: system-image-snappy-cli mas não será instalado
                       Depende: ubuntu-snappy mas não será instalado
E: Impossível corrigir problemas, você manteve (hold) pacotes quebrados.
```
[COLOR=#111111][FONT=Ubuntu]
I guess I don't as much as I should to solve this. Can anyone give me a hint on how to fix this, please?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Thanks![/FONT][/COLOR]

---

### Post by cariboo on 2015-06-27
You are not going to get things to work with Unity8 installed. You need to remove it  before you can do anything else.

```
sudo apt-get purge unity8
```

---

### Post by grahammechanical on 2015-06-27
Did you upgrade from an existing installation of Ubuntu 14.10? How did you do that? Or did you upgrade in the sense of installing Ubuntu Wily Werewolf (15.10).

I think that you downloaded and installed Ubuntu Desktop Next ISO image. That is not Ubuntu desktop. It is the Ubuntu phone OS on the desktop and we may have problems if we are using a proprietary video driver. I stopped testing Ubuntu Desktop Next back in May because I could not get past the login screen. It always came up with a black a screen.

At the moment this is the right place to download Ubuntu wily werewolf (15.10). Try wily-desktop-amd64.iso

[http://cdimage.ubuntu.com/ubuntu/daily-live/current/](http://cdimage.ubuntu.com/ubuntu/daily-live/current/)

This is the wrong place. Notice the newest ISO image is from 29 May.

[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/)

We are awaiting new ISO images of a future Ubuntu desktop that runs on Mir and has Unity 8 and Snap packaging instead of running on X and Unity 7 and deb packaging as Ubuntu does at present. Whether it will be called desktop-next or something else is a matter for people to argue over. We will not know until these new ISO images appear at cdimage.ubuntu.com. But when they appear someone will post a thread about it and you can then join with the rest of us in testing it.

Regards.

---

### Post by raphaeldc on 2015-06-27
Sorry, I guess I wasn't clear enough... I had 15.04 and upgraded (do-release-upgrade -d) to 15.10... After that, unity was gone... Had to install MATE. It's not that I don't like it, but MATE does not work like unity in my laptop... That's the reason I wanted to bring unity back.

---

### Post by PaulW2U on 2015-06-27
In that case it's not totally clear how *unity8* became installed.

Have you tried to remove it as cariboo suggested? Can you remove it or do you get further errors?

---

### Post by kansasnoob on 2015-06-27
You might see what happens with:

```
sudo apt-get install ubuntu-desktop -s
```

The -s suffix will only simulate what would happen and might indicate what package conflicts might exist.

---

