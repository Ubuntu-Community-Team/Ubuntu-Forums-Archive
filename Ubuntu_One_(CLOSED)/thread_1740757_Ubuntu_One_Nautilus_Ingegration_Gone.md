---
title: "Ubuntu One Nautilus Ingegration Gone"
date: 2011-04-27
forum: Ubuntu One (CLOSED)
---

### Post by aaaaalex on 2011-04-27
Running U1 on Natty. Last thing changed was: Enabling a few Nautilus Scripts (via UbuntuTweak, just seems to copy the scripts to the respective Nautilus scripts folder though).

Some time later i noticed all my nautilus/ U1 integration having disappeared (see screen shot).

I cleared out the Nautilus scripts folder, and purged everything in relation to U1 from Synaptic and re-installed... Still the indicators and the context sensitive menu are gone.

U1 however does still work. I can synchronize just fine - i just cant control it any longer with right click.

Is there a way to bring this feature back? Maybe a configuration switch somewhere. Have not found anything yet.

---

### Post by duanedesign on 2011-04-28
Lets see if this is happening because 'ubuntuone-client' is not running or it is something else. Can you run the following command from a terminal.

```
ps aux | grep ubu
```

Do you see something like the following?

```
1000 19394 55.0  5.9 575228 169576 ?  Sl 14:39  0:56 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon

```
[COLOR="Green"]YES[/COLOR]
If you do see this process can you now check and see if the context menu options for Ubuntu One are available.
[COLOR="Red"]NO[/COLOR]
If you do not see it you can start the client by opening the Ubuntu One control Panel from the launcher. Give it a second to start and then run the command again to make sure the client is started. Then check for the context menu options.

I am trying to determine if the process is running **and **you do not see the context menu.

thank you,
duanedesign

---

### Post by aaaaalex on 2011-04-28
Thank you for picking this up.

Unfortunately its no longer possible to investigate this issue further as i just installed the final Version of Natty over my Beta Testing partition. I messed too much with it.

The Ubuntuone Client Gui was running, also files were syncing fine - even had the notifications. 

If this happens again later as I fiddle with nautilus context sensitive menu we can pick up here. 

For now: Solved

---

### Post by straki on 2011-05-02
Hi,
thanks for starting this, I have the same problem. ubuntuone-client is running, 

```
742  1.6  1.7 112244 34680 ?        Sl   21:27   0:30 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
```

and I can drop files in the Ubuntu One folder and it synchronizes ok, notifications work. But I can't synchronize outside the Ubuntu One folder, because Ubuntu One does not appear in the context menu in nautilus. 

And I'd rather not do a clean install like aaaaalex .... :)

thank you

---

### Post by kost_bebix on 2011-05-07
Ok, the solution is:

sudo apt-get install ubuntuone-client-gnome

---

### Post by selectstar on 2011-05-22
I am having the same issue and wasn't able to solve it with any of the proposed solutions in this thread. Any ideas?

---

### Post by viktor- on 2011-05-31
Same problem here. Using 11.04 classic version.

---

### Post by duanedesign on 2011-05-31
You have confirmed that syncdaemon is running with the command

```
ps aux | grep ubu
```

Is their no Ubuntu One entry when you right-click on a folder in your $Home, or is their an entry for Ubuntu One but it is that 'Synchronise this folder' option is greyed out?

thank you,
duanedesign

---

### Post by viktor- on 2011-06-01
Thanks for the reply but I got it to work now. Dont ask me how though, suddenly the Ubuntu one entry just appeared in the menus as they should.

---

### Post by martijn1985 on 2011-06-22
sorry for bumping this thread, but I have the same problem. However, the syncdaemon is NOT running. I'm running on Maverick

```

martijn@martijn-GA-MA78GM-S2H:~$ ps aux | grep ubu
martijn   1847  0.0  0.0   1900   508 ?        S    21:47   0:00 /bin/sh -c [ -d "$HOME/Ubuntu One" ] && ubuntuone-launch
martijn   1848  0.1  0.3  22212 15244 ?        S    21:47   0:00 /usr/bin/python /usr/bin/ubuntuone-launch
martijn   1941  0.2  0.5  36016 21084 ?        SL   21:47   0:00 /usr/bin/python /usr/lib/ubuntu-sso-client/ubuntu-sso-login
martijn   2397 11.8  0.7 107720 29572 ?        S    21:50   0:00 /usr/bin/python /usr/bin/ubuntuone-preferences
martijn   2479  0.0  0.0   4032   752 pts/0    S+   21:50   0:00 grep --color=auto ubu

```

So I tried ```
sudo apt-get install ubuntuone-client-gnome
```, which installed something, but that didn't help. What would be the next step?

---

### Post by pikamoku on 2011-07-06
bump!

my system:
- natty 64bit + gnome-shell(gnome3) 
- ubuntuone daemon working and updating folders content

but lost Nautilus (3.0.2) integration (right click menu) to publish, create link,etc

annoying but not critical :(

---

### Post by martijn1985 on 2011-07-06
I got my problem fixed a while ago, sorry for not posting the solution.

I had to google a bit, but I found this thread: [http://ubuntuforums.org/showthread.php?t=1468824&page=5](http://ubuntuforums.org/showthread.php?t=1468824&page=5)
where someone suggests deleting ~/.local/share/ubuntuone. I think I tried that, and after that it worked again. It may have been due to me downgrading from Natty to Maverick, I don't know.

---

### Post by duanedesign on 2011-07-11
Yes, if you downgrade the newer metadata will not work with the older client. See[ bug 517505]("https://bugs.launchpad.net/ubuntuone-client/+bug/517505")

Thank you for updating your thread with your fix.

respectfully,
duanedesign

---

