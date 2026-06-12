---
title: "Wine and virus's"
date: 2010-05-02
forum: Security
---

### Post by pcrat on 2010-05-02
Just wondering.. if i run a program that is infected with a trojan/virus in Wine will it effect Ubuntu?

---

### Post by Chlodovechus on 2010-05-02
If you use Wine on an application with malware it can effect Ubuntu, but  I don't know exactly  how it will.

---

### Post by sunk8 on 2010-05-02
You can also install an anti-virus inside WINE.

---

### Post by Rubi1200 on 2010-05-02
First of all read bodhi.zazen's security sticky!

Secondly, ask yourself if you really, really need WINE

Thirdly, 
from the sticky I mentioned above:
[SIZE=2][/SIZE]> [SIZE=2]_A few comments on wine_[/SIZE]

Discussions about running Windows viruses on wine crop up from time to time and it is possible to run some Windows viruses on wine.

See these links :
[LIST]
[*][McAfee Avert Labs Blog]("http://www.avertlabs.com/research/blog/index.php/2009/02/23/running-windows-malware-in-linux/")
[*][Running Windows viruses in wine]("http://www.linux.com/articles/42031")
[/LIST]

So what do you need to know about Windows viruses if you want to run wine?

1. First, the "golden rule" : [COLOR=darkred]**DO NOT RUN WINE AS ROOT**[/COLOR]. If you are **NOT** running wine as root then wine will not have the necessary permissions to affect system files.

2. So, if you are running wine as a user, a Windows virus will be confined to your home directory.

3. You can further confine the "fake c drive" located at ~/.wine if you remove any symbolic links outside ~/.wine. With a default installation there is link with a default installation / configuration of wine :
[LIST]
[*]~/.wine/dosdevices/z: -> links to /
[/LIST]

A link from ~/.wine/dosdevices to the root directory ( / ) should concern you for obvious reasons.

You can remove it with :

     Code:
     unlink ~/.wine/dosdevices/z: 
Do not worry, that command will not affect wine at all, I run it all the time :twisted:

You may need to make a link in ~/.wine/dosdevices to your cdrom and/or you may be tempted to link to your home directory, but I advise against keeping using these links (beyond the time needed for actually installing applications).

I advise against any links to removable devices (it should not be *that* difficult to copy files needed to the appropriate location in ~/.wine/drive_c ).

4. Consider running an antivirus program and scanning ~/.wine and any removable devices or other locations you use outside of ~/.wine to store programs or data to be used with wine. Scan any data / applications you use with Windows.

5. Consider confining wine with Apparmor. 

6. Be sure to file a bug report with the wine project as they have a very active security team (it is unrealistic, however, to expect the wine team to be able to protect you from all Windows viruses all the time). [Wine Bug Reports]("http://bugs.winehq.org/")

7. Take the same precautions with wine as you would with Windows. Do not install untrusted applications from untrusted sources.

If you follow the above advice, Windows viruses will be confined to ~/.wine and they do not have permission to change system files. This means to remove them you simply:

     Code:
     rm -rf ~/.wine 
[COLOR=darkred]Please take care, this command deletes everything in your wine directory including all data and all applications.[/COLOR]

You then need to restore your wine directory from a known good backup (you do keep backups ?).

---

### Post by kmrs75 on 2010-05-04
well i have been trying this becouse i didnt know - 

i have a few programs that i know have viruses in them and i am running them in wine for 2 months now and i havent seen any kind of problems with anything. i cant recall the viruses at this time but i do know in a windows computer there nasty. web links to adults sits on my desktop that i couldnt ever get rid of, computer would reboot, it would lock up, and i havent seen a thing yet. 

so my opinion of testing it unless its a very bad virus i dont see it happening. 

o my bro put just one of the programs on his computer 1 week later he has to a format. 2xs he did that then gave up

---

### Post by cipherboy_loc on 2010-05-04
After I removed all links to folders out side of ~/.wine in the ~/.wine/drive_c/users/<username>/ directory, I then created new folders with nothing in it. Then when I use a file in a program running under WINE it will save to the ~/.wine/drive_c/users/cipherboy/My Documents, and once I make sure it has no viruses, I can copy it to a flash drive, or directly to my Windows XP partition.

---

### Post by cariboo on 2010-05-04
I have to ask, if you have programs with viruses embedded in them, why use them? And why pass them on to others?

---

### Post by doas777 on 2010-05-04
it depends entirely on what api calls the malware makes, and whether they are correctly implemented in wine. it also depends on what resources the malware wants to work with, since installing a rootkit in wine is essentially useless, and since the other host processes are outside of wines domain, it would be hard to run a keylogger the way you would in windows, because the apps you want to log aren't running in wine.

---

### Post by lisati on 2010-05-04
Check out what Wine has access to. On the rare occasions I've started Wine, it has, by default, had access to what it refers to as "Z:", which maps to "/" on my Ubuntu install. I've usually disabled this by running winecfg and unchecking the relevant box.

---

### Post by Animal X on 2010-05-04
> **cariboo907 said:**
> I have to ask, if you have programs with viruses embedded in them, why use them? And why pass them on to others?
experimental self-mutilation can manifest itself many ways...as far as passing them on to others-it is his bro, lol.

---

