---
title: "Recover user data from reinstalled drive..."
date: 2010-04-03
forum: Security
---

### Post by Angelstouch on 2010-04-03
Hello, I reinstalled Ubuntu after some issues with my nvidia-drivers.](*,)
And now I really need help to retrieve my old users data.[-o<
Please excuse my poor english but it's not my native language,
I had to kind a recreate the error messages since they were half in my native language and half in english.:roll:
 I'm using Karmic Koala 9.10 which I upgraded from 9.04.
After lots of tries and errors,I decided to use a solution someone postet in another forum: Just reinstlling on the same drive without formating the disk.
I kept the filestuctur EXT4, set the mounting point to "/" and used the same maschinename,username and password as before.
While the installation I received an error message from **ecryptfs-utils**. Now I have a broken package in synaptics and am not able to deinstall it nor install anything else with synaptics.
During login I'm told that** .ICEauthority** can't be updated:
**Could not update ICEauthority file /home/username/.ICEauthority**
and after that:
**There is a problem with your configurationserver. ****(/usr/lib/libgconf2-4/gconf-sanity-check-2 ended with Status 256)**
And then:
**Nautilus couldn't create the nescessary folder: /home/username/Desktop, /home/username/.nautilus. Please create the following folders before you start Nautilusor change the rights so Nautilus can create it.**
And then nothing happens anymore, there is just my mousecursor in front of the backgroundpicture.:-k
If I change with STRG+ALT+F1 to the terminalI'm able to login but I'm not allowed to see my folder **/home/username** I get the message:
**-bash: cd: username: Permission denied**
I tried in recovery-mode:
**root@****[B]maschinename**[/B][B]:/su username
[/B]but received[B]:
bash: /home/username/.bashrc: Permission denied[/B]
**username@****[B]maschinename**[/B]**:/$**  
then I tried to get back to root with:
[B]username@maschinename:/su root  
[/B]but all my passwords were refused and I'm not sure if I created a root-password at all when I first installed Ubuntu, but even with no password I got the same result:
**su: error with the authentication**
Maybe when I reinstalled my system I used "**Maschinename**" instead of "**maschinename**".

If I start from my Live-CD Karmic 9.10 and go to the folder /home/username and try to use **Access-Your-Private-Data.desktop** the terminal only pops up and vanishes right away.I have a folder with "**.Private**" but no folder called "**Private**"

             I also tried the following commands:

**root@****[B]maschinename**[/B][B]:/home/username# sudo ecryptfs-add-passphrase
[email]root@[/B]**[B]maschinename**[/B]**:/home/username/.Privat[/email]**[B]e# sudo ecryptfs-add-passphrase
root@[/B]**[B]maschinename**[/B][B]:/home/# sudo ecryptfs-add-passphrase
root@[/B]**[B]maschinename**[/B][B]:/# sudo ecryptfs-add-passphrase
[/B]everytime the response is:
[B]ecryptfs-add-passphrase: error while loading shared libraries: libecryptfs.so.0:
cannot open shared object file: No such file or directory[/B]
Also tried the following with little luck:
**root@maschinename:# ecrypt-unwrap-passphrase home/username/.ecryptfs/wrapped-passphrase "**********"**
( ...where the ******** are my password [IMG]http://media.ubuntuusers.de/wiki/attachments/09/28/wink.png[/IMG]  ... ) I also tried:

**root@maschinename:# ecrypt-unwrap-passphrase /home/username/.ecryptfs/wrapped-passphrase "**********"** 
    and some other combinations the response was always: 
**ecrypt-unwrap-passphrase: error while loading shared libraries : libecryptfs.so.0: cannot open shared object file: No such file or directory**
Is it possible that by using the same username on the 2nd installation all neccessary files have been deleted or has the error with **ecryptfs** during the 2nd installation prevented further damage to my files.
Kind of in the way of "**already exsists so I don't write over it**" [-o< ?

I created a new user with admin rights but if I start synaptics it tells me that
ecryptfs-utils has errors in its dependencies and I get the following error message:

**E:ecryptfs-utils:sub-process installed pre-removal-script returned error-data 1**in the terminal the error reads like this: 
[B]ERROR:Cannot remove ecryptfs-utils, as it appears to be in use:
[/home/**username**/.ecryptfs]
dpkg: error while working on ecryptfs-utils (--remove)
E: Sub-process /usr/bin/dpkg returned an error code (1)
During package installation errors have acured, trying to solve it:
[/B]while **[B]user**name[/B] is the user I want to restore not the new one.
I also tried with my Live-CD Karmic 9.10: 
[B]ubuntu@ubuntu$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# su - username
**Unbekannte ID: user**[/B][B]name
root@ubuntu:/#
[/B]I'm able to connect to my 2nd user like this, but not to the one I'd like to restore the data of.I really need these files back, since I didn't make any backups (I know: some people never learn.:()

Thx in advance everyone, hope you can help me save my data...

[-o<

---

### Post by Angelstouch on 2010-04-03
Has really noone an idea, that could help me?
Or could someone maybe tell me, if there is a chance or if my stuff is definetly gone.

Thx in advance...Angelstouch...:popcorn:

---

### Post by cariboo on 2010-04-03
The only think I can think of, is that it may be permissions issue. Are all the files in the home directory in question owned by you and have permissions of 755 or 700?

---

### Post by Angelstouch on 2010-04-03
I actually don't know.
Is that the thing I can change with chown?
by the way thx for the answer, that sounds promissing #-)

I've looked a little into chown and chmod, but they're quite confusing for me,since I am a noob to ubuntu.
I would be very gratefull if you could give me a little (or even alot of O:) ) guidance on this matter, since
I don't want to mess up my entire system and really be left without my whole data.

Here is what I've done so far then and the infos I think might be helpfull: :grin:

```
ubuntu@ubuntu:~$ id
uid=999(ubuntu) gid=999(ubuntu) Gruppen=4(adm),20(dialout),24(cdrom),46(plugdev),104(lpadmin),115(admin),120(sambashare),999(ubuntu)

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /dev/shm /mnt/dev/shm
ubuntu@ubuntu:~$ udo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# su - user2restore
Unbekannte ID: user2restore
root@ubuntu:/# id
uid=0(root) gid=0(root) Gruppen=0(root)
root@ubuntu:/# fdisk -l

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1       29650   238163593+  83  Linux
/dev/sda2           29651       30401     6032407+   5  Erweiterte
/dev/sda5           29651       30401     6032376   82  Linux Swap / Solaris

```What I don't know is how to find out the uid of "user2restore",
the actual uid of the owner of a folder like my folder /home/user2restore on sda1
and then how to change it so my ubuntu@ubuntu with uid (999) kann read it and save it
to a backup dir.
Of course I know the login password for my "user2restore" but is that enough?
Are there no more issues with ecryptfs-utils then?
At the moment I start my system with a Live-USB and mount my old drive as shown above.

Thx in advance again.
You are really giving me hope again,[-o<
Dear cariboo907,I have to thank you alot, cause I was totally at a deadend there.

yours...Angelstouch...):P

---

### Post by Angelstouch on 2010-04-03
Hm, changed the owner of all the files in /home/user2restore with

root@ubuntu:/home$ chown -R newuser user2restore

Now "newuser" is able to enter the folders of "user2restore",
but it's still only the :
Access-Your-Private-Data.desktop and README.txt
apart from the  few hidden directories like .Private and .ecryptfs

and I still can't unwrap the passphrase and on the GUI the Access-Your-Private-Data.desktop of "user2restore" just pops up and vanishes again.

D... I was so sure it would work...](*,)

Anymore ideas ;)

Again thx in advance...

---

### Post by cariboo on 2010-04-03
You have to use the user name of the person who created the data eg:

```
sudo chown -R Angelstouch:Angelstouch /home/Angelstouch
```

then set the permissions

```
sudo chmod -R 755 /home/Angelstouch
```

you should get an error saying can't change ownership or permissions for .gvfs, but everything else should be OK.

---

### Post by Angelstouch on 2010-04-04
Thx, again cariboo907,

if I do
```
root@ubuntu:/# sudo chown -R user2restore:user2restore /home/user2restore
```I only get:
```
chown: invalid user: &#8222;user2restore:user2restore&#8220;

```Sorry, for causing so much trouble :oops:
Seems when I mess up, I mess up good.:neutral:

Maybe I can add a user with the name of "user2restore" to my Live-USB and then transfer the ownership to it?

Thx, again ... Angelstouch ...

---

### Post by Angelstouch on 2010-04-13
Is it in any way maybe possible to restore a valid user for my "user2restore", I mean if I create a new user with the same  name and the same password?
Maybe anyone another idea?

Lots of thx...Angel...

---

### Post by krazyjvc on 2010-04-14
Hi angel,
I have this very same problem with my ubuntu (re)installation in my ol' Dell C400. I had intrepid and have happened the same thing as you when i've upgraded. it's been a while since then, but a time ago i've created a new account in /home and kept the original login untouch (i hope) so i can get those damn files one day.
Now i'm using karmic for the last days until upgrading do lucid and every time i login with krazy (my "user2restore") i have that .ICEauthoity error and nautilus and... and... same thing.
if i can help in anything i'm here. Good luck for us all.
[[ ]]

---

