---
title: "Strange Terminal commands! Easter eggs Post em."
date: 2009-09-23
forum: The Cafe
---

### Post by peterthinking on 2009-09-23
I've run into a few strange ones....what are your favorites?
I like this train

sudo apt-get install sl

enter then type

sl

in terminal

sl -l

in terminal makes a longer one!

This one makes star wars run in your terminal?!?

telnet towel.blinkenlights.nl

peterthinking

---

### Post by SuperSonic4 on 2009-09-23
[COLOR="Red"]THIS ONLY WORKS ON ARCH LINUX[/COLOR]

```
pacman --version
```

Put ```
ILoveCandy
``` in ```
/etc/pacman.conf
``` and run ```
sudo pacman -Syyu
``` :p

---

### Post by dragos240 on 2009-09-23
> **SuperSonic4 said:**
> ```
pacman --version
```Put ```
ILoveCandy
``` in ```
/etc/pacman.conf
``` and run ```
sudo pacman -Syyu
``` :p

Must try.....

---

### Post by SuperSonic4 on 2009-09-23
> **dragos240 said:**
> Must try.....

Ensure ILoveCandy is before the repository section though:

```
# Misc options (all disabled by default)                                                                                                                                         
#NoPassiveFtp                                                                                                                                                                    
#UseSyslog                                                                                                                                                                       
ShowSize                                                                                                                                                                         
#UseDelta                                                                                                                                                                        
TotalDownload                                                                                                                                                                    
**ILoveCandy   **                                                                                                                                                                    
                                                                                                                                                                                 
#                                                                                                                                                                                
# REPOSITORIES   
```

---

### Post by dragos240 on 2009-09-23
> **SuperSonic4 said:**
> ```
pacman --version
```Put ```
ILoveCandy
``` in ```
/etc/pacman.conf
``` and run ```
sudo pacman -Syyu
``` :p

Odd....

```

[root@localhost ~]# pacman -Syyu
error: config file /etc/pacman.conf, line 77: directive 'ILoveCandy' not recognized.

```

---

### Post by SuperSonic4 on 2009-09-23
> **dragos240 said:**
> Odd....

```

[root@localhost ~]# pacman -Syyu
error: config file /etc/pacman.conf, line 77: directive 'ILoveCandy' not recognized.

```

See my edit xD. I forgot that bit xD. You could run any pacman command. I just picked -Syyu because it will show you for sure

---

### Post by Mike'sHardLinux on 2009-09-23
> **peterthinking said:**
> 

This one makes star wars run in your terminal?!?

telnet towel.blinkenlights.nl

peterthinking


That is pretty cool, but it isn't an easter egg or strange command, any more that going to a cool website is. You are just telnetting into someone's server. 

Still a pretty cool server though....

---

### Post by peterthinking on 2009-09-23
Nice! I got the pacman game running but couldn't find a pacman.conf file to put ILoveCandy into

---

### Post by dragos240 on 2009-09-23
Hmm..... I just did that. I didn't see anything:

```

[root@localhost ~]# pacman -Syyu
:: Synchronizing package databases...
 core                      33.7K   68.5K/s 00:00:00 [---------------------] 100%
 extra                    429.3K  109.2K/s 00:00:04 [---------------------] 100%
 community                365.3K  120.0K/s 00:00:03 [---------------------] 100%
:: Starting full system upgrade...
 local database is up to date

```

---

### Post by dragos240 on 2009-09-23
> **peterthinking said:**
> Nice! I got the pacman game running but couldn't find a pacman.conf file to put ILoveCandy into

You need to be running archlinux.

---

### Post by SuperSonic4 on 2009-09-23
Your computer is probably too fast haha. Note that the [######] is now [------] though :p

---

### Post by dragos240 on 2009-09-23
> **SuperSonic4 said:**
> Your computer is probably too fast haha. Note that the [######] is now [------] though :p

I see. Small difference. You should also tell the ubuntu users you need to be running archlinux. They think you're talking about PacMan. The game.

---

### Post by peterthinking on 2009-09-23
This isn't about the pacman game?

---

### Post by SuperSonic4 on 2009-09-23
> **dragos240 said:**
> I see. Small difference. You should also tell the ubuntu users you need to be running archlinux. They think you're talking about PacMan. The game.

There is a difference, I have a screenshot (although it's animated so hard to see really lol) but I won't put it up unless someone asks

> **peterthinking said:**
> This isn't about the pacman game?

No, pacman is the package manager in arch. It does the same function as apt in ubuntu. The OP did not specify which OS so I put in an arch one ;)

---

### Post by dragos240 on 2009-09-23
> **peterthinking said:**
> This isn't about the pacman game?

Nope. It's a package manager for archlinux. Much like apt-get is to ubuntu and debian.

---

### Post by A_Fiachra on 2009-09-23
```

$ find . -name "*.py" | xargs grep "re\." | awk -F: '{ print $2 }' | sed -r "/^\s/d" | sort -u
```

---

### Post by A_Fiachra on 2009-09-23
oop -- no Easter Egg ... just strange

---

### Post by dragos240 on 2009-09-23
I saw it! It's a yellow 'C' eating 'o's much like PacMan eats those dots. *Nice!*

---

### Post by peterthinking on 2009-09-23
> **dragos240 said:**
> I saw it! It's a yellow 'C' eating 'o's much like PacMan eats those dots. *Nice!*

So this is safe to run in terminal?

find . -name "*.py" | xargs grep "re\." | awk -F: '{ print $2 }' | sed -r "/^\s/d" | sort -u


 looks kinda cryptic to me, hard to trust it

---

### Post by peterthinking on 2009-09-23
This one is cool too.

Have your computer make random beeps while it's locked and you're at lunch!

Cut and paste this into a terminal...

while true; do sleep $(($RANDOM/1000)) && beep -f 2000 -l $(($RANDOM/100)) ; done

Or....

while true; do sleep $(($RANDOM/5000)) && beep -f $((RANDOM/10)) -l $(($RANDOM/100)) ; done


control c in terminal to stop it.

you'll have to sudo apt-get install beep if you don't have it.

---

### Post by wojox on 2009-09-23
Open Firefox and type in the navigation bar:

```
about:Mozilla
```

---

### Post by sisco311 on 2009-09-23
classic:
```
apt-get moo
aptitude moo
aptitude -v moo
aptitude -vv moo
aptitude -vvv moo
...

```

---

### Post by sisco311 on 2009-09-23
> **wojox said:**
> Open Firefox and type in the navigation bar:

```
about:**robots**
```

fixed :)

---

### Post by wojox on 2009-09-23
> **sisco311 said:**
> fixed :)

Thats a good one. :lolflag:

---

### Post by peterthinking on 2009-09-23
> **Mike'sHardLinux said:**
> That is pretty cool, but it isn't an easter egg or strange command, any more that going to a cool website is. You are just telnetting into someone's server. 

Still a pretty cool server though....

One more thing...after Luke rescues Leia she freaks out and starts dancing and singing Never gonna give you up by Rick Ashley.
True story...I just sorta left it running and was like "Whaaaaat?"

---

### Post by dragos240 on 2009-09-23
Rick *Astley*

---

### Post by hansdown on 2009-09-23
Type```
 free the fish
``` in the terminal.

If you like goldfish, enjoy.

To stop it swimming across the desktop, type```
 killall gnome-panel
```

---

### Post by clonne4crw on 2009-09-23
> **sisco311 said:**
> classic:
```
apt-get moo
aptitude moo
aptitude -v moo
aptitude -vv moo
aptitude -vvv moo
...

```

Awww. I was gonna post that.

---

### Post by t0p on 2009-09-23
Type into a terminal:

```
ddate
```If you're all like wtf? then run

```
man ddate
```of course.  And Hail Eris!   :p

---

### Post by peterthinking on 2009-09-24
> **hansdown said:**
> Type```
 free the fish
``` in the terminal.

If you like goldfish, enjoy.

To stop it swimming across the desktop, type```
 killall gnome-panel
```

Alt + F2 then "free the fish"

free the fish in Terminal gives me this

peter@peter-desktop:~$ free the fish
             total       used       free     shared    buffers     cached
Mem:        477164     364832     112332          0      24272     136972
-/+ buffers/cache:     203588     273576
Swap:      1405648      27004    1378644

---

