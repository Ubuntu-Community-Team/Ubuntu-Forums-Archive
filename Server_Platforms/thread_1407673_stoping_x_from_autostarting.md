---
title: "stoping x from autostarting??"
date: 2010-02-15
forum: Server Platforms
---

### Post by seniortaco on 2010-02-15
Ok so I just installed Ubuntu server 9.10. It started out as cmd line only, I ended up installing ubuntu-desktop package from apt. 
I ran startx, and from that point on when ever I start the server I get the gui login screen instead of the original cmd line prompt. 

Now Ive been surfing around the net trying to figure out how to get it back to the original cmd prompt login screen, I really want to use startx when i need a gui.. the main reason I installed this package is really for all the libraries that it contains as i will use a few programs (firestarter, powertweak etc) that use a gui and I figured to make my life simpler i would just install the entire gnome desktop package so i will have everything i need when i try to run these misc programs (most of them will be run thru x11 forwarding as this server will only have internet and power plugged into it) 

Ive tried disabling gdm startup Ive even removed the /etc/init.d/gdm file all together and it still starts X (i moved it to /usr really but it should(?) work the same as deleting it). there is no other desktop manager to my knowledge (kdm etc).
Ive tried rcconf it says gdm is disabled (i tried disabling it before removing gdm from init.d and nothing), I went thru trying to disable anything that has to do with xserver so far I have only found x11-common I dont think it starts up x but i disabled it anyway. 

Ive also tried "[FONT=Verdana]update-rc.d -f gdm remove" that doesn't do anything either seems no matter what i try i cant stop the gui login screen from popping up.. 

How do i get it to start with the original cmd prompt login?? i am considering reinstalling to get it back but i will lose all my work and that will defeat the purpose..

Thanks alot in advanced guys
[/FONT]

---

### Post by Satoru-san on 2010-02-15
```
sudo update-rc.d gdm remove
```

you might have to use -f to force or do this first

```
killall Xorg
--or---
sudo /etc/init.d/gdm stop
```

---

### Post by seniortaco on 2010-02-15
> **seniortaco said:**
> 
Ive also tried "[FONT=Verdana]update-rc.d -f gdm remove" that doesn't do anything either seems no matter what i try i cant stop the gui login screen from popping up.. 
[/FONT]
  I have already tried that cmd it doesnt seem to help ive tried it with the force and without it same results. Just a note when i do sudo killall Xorg, xserver will restart anyways ive tried this from the computer its self and thru ssh

on a side note for some reason i cant access mysql server from any remote machine and when i try one of the mysql management tools on the actual machine (using the local ip 192.168.1.48 ) i cannot connect either but if i do mysql -u root -p and the password i can connect to it and edit users etc any reason to this?? ive already opened the ports needed and ive even tried shutting the firewall off all together.. I may post this one in a separate thread if i need to.  All ive done is run "sudo apt-get install mysql-server" and set a root password when it asked, loged in using the mysql cmd and set my users up.

---

### Post by seniortaco on 2010-02-15
an update on that mysql thing it works by connecting to the loop back (127.0.0.1) how do i set mysql to run off eth0 and not (or both it doesnt matter) the lo interface??

---

### Post by sisco311 on 2010-02-15
Use gufw instead of firestarter. firestarter is no longer actively maintained or updated. 

[uhelp]community/Firewall[/uhelp]


In order to boot in the CLI, edit the /etc/default/grub file & replace the 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
line with
```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```
then run:
```
sudo update-grub
```

EDIT:
Check the community documentation about MySQL:
[uhelp]community/ApacheMySQLPHP#After%20installing%20MySQL[/uhelp]

---

### Post by seniortaco on 2010-02-15
> **sisco311 said:**
> Use gufw instead of firestarter. firestarter is no longer actively maintained or updated. 

[uhelp]community/Firewall[/uhelp]


In order to boot in the CLI, edit the /etc/default/grub file & replace the 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```line with
```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```then run:
```
sudo update-grub
```EDIT:
Check the community documentation about MySQL:
[uhelp]community/ApacheMySQLPHP#After%20installing%20MySQL[/uhelp]
  
OMG OMG I LOVE U SISCO! IT LIVES MUAHAHAHHAHAHAHAHHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHA..

Sorry i get over excited some times :P but that did the trick!!! 

Now if only someone can help me figure out how to make mysql run on the eth0 interface (if that is indeed the problem, it sure seems like it).

Edit: missed that link there i will try checking it out but if anyone knows how off the top of thier head that will be awesome to 8)
Edit agian....: yah it was like the first line i read :P so nvr mind,  sisco once agian u dee man

---

### Post by seniortaco on 2010-02-15
ok so ive binded the address and it still doesnt work BUT when i stop mysqld and start it agian (using sudo mysqld) it works..  when i restart the computer i run into the same issue ive got to  "sudo mysqld stop" then "sudo mysqld" and then i can connect.. ?? whats going on ?

---

