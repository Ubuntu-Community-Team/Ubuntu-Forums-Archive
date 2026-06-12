---
title: "help with tor-polipo (/etc/polipo/config)"
date: 2010-03-27
forum: Security
---

### Post by hihihi100 on 2010-03-27
Hello:

Im installing both tor and polipo according to the instructions found at:

[https://www.torproject.org/docs/tor-doc-unix.html.en#polipo](https://www.torproject.org/docs/tor-doc-unix.html.en#polipo)
[SIZE=1]
Namely: 
[/SIZE]**[SIZE=1][Step Two: Install Polipo for Web Browsing]("https://www.torproject.org/docs/tor-doc-unix.html.en#polipo")[/SIZE]**

[SIZE=1]Grab our [Polipo configuration for Tor]("https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf") and put it in place of your current polipo config file (e.g. /etc/polipo/config or ~/.polipo).[/SIZE]

What exactly do I have to type in the terminal? sudo wont make any difference

Help please

cheers

---

### Post by mkvnmtr on 2010-03-27
I do not type very well and screw up nearly every time.So what I did was open computer/file system /ect/ polipo. Then the terminal. I typed sudo gedit and hit the space bar. Then I dradded the configure file to the terminal and hit enter. This opened the file in gedit. I then coppied the file to the desktop as a back up. Then I deleted it in gedit and replaced it by dragging the tor configurition to gedit. Then when I closed it Icnoose to save it. Then I typed exit in the terminal and pressed enter. I also did it using mouspad several times on other systems. 

Then I tried tor button several times. On all my systems it never worked until I restarted.

---

### Post by hihihi100 on 2010-03-28
do u speak spanish?

---

### Post by Ijan on 2010-03-28
My guess:

First you download the linked config-file to your local system, typically to ~/Downloads

Then you rename the existing config file /etc/polipo/config
You can do all the following in your graphical environment via Nautilus by starting via the command line with "gksu nautilus" or you type
> sudo mv -i /etc/polipo/config /etc/polipo/config.old
Then you copy the downloaded file in the place of the old one you just renamed.
> sudo cp -i ~/Downloads/polipo.conf /etc/polipo/config

Now you restart polipo to load the new configuration by typing:
> sudo /etc/init.d/polipo restart

(Keep in mind that using the previous versions of the tor package you also had to remove Privoxy or reconfigure it not to use the Socks standard port. You can check if Privoxy is still running by "sudo ps -A | grep -i privoxy")

This is how I remember it. Hope it works.

---

### Post by hihihi100 on 2010-03-28
Hi Jan, not really sure if I have done it the right way: this is what I have done via terminal:
```
hihihi100@hihihi100-laptop:~$ sudo mv -i /etc/polipo/config /etc/polipo/config.old 
_mv: overwrite `/etc/polipo/config.old'? y_
hihihi100@hihihi100-laptop:~$ sudo mv -i /etc/polipo/config /etc/polipo/config.old 
mv: cannot stat `/etc/polipo/config': No such file or directory
hihihi100@hihihi100-laptop:~$ sudo cp -i ~/Downloads/polipo.conf /etc/polipo/config 
hihihi100@hihihi100-laptop:~$ sudo /etc/init.d/polipo restart 
Restarting polipo: polipo.
hihihi100@hihihi100-laptop:~$ 

```Please take a look at the underlined section (overwrite), I typed an Y as when Im asked to confirm-deny something, but Im usually propmted do do so (type yes or no), so Im not sure if I have done it the right way...

regards

It seems it works, I just made a tor test, and it says Im using it...

Can I now install Privoxy? Have u both polipo and privoxy in use? (not at the same time, obviously, but, do u use both on alternate times?

thx...

---

### Post by Ijan on 2010-03-28
That output looks like you didn't have a deafault "config"-File in /etc/polipo/. You can post the output of "ls -l /etc/polipo/" and "ls ~/.polipo/" if you like.

Anyhow it seems to work (did you use the Tor-detector web page or what does say you are using it?) and if Polipo's inital config-file was placed elsewhere polipo should use the one above now.

Polipo/Privoxy: Both do more or less the same, so the question if trying both and changing to and fro makes sense depends on what you're out for. It would involve some more learning about setting up a proxy and configuring your Browser/Tor to use it. If you are prepared to do so, go ahead. Privoxy has AFAIK some more filtering/rewriting capabilities compared to Polipo but the latter is definitely fine and designed to be set up easily and maintained by the Tor-developers to work flawlessly with Tor. So if you just want to have Tor running you can simply keep Polipo.

The "Privacy" part in "Privoxy" is for a big part taken care of by "Torbutton" so you don't need Privoxy to have any privacy. In that field learning what Tor does and what it not does - magically securing unencrypted/insecure application traffic - might better serve your privacy at this point.

---

### Post by hihihi100 on 2010-03-28
like this?

```
hihihi100@hihihi100-laptop:~$ ls -l /etc/polipo/
total 16
-rw-r--r-- 1 root root 3904 2010-03-28 20:57 config
-rw-r--r-- 1 root root 3904 2010-03-28 20:55 config.old
-rw-r--r-- 1 root root  450 2010-03-16 17:03 forbidden
-rw-r--r-- 1 root root  172 2010-03-16 17:03 options
hihihi100@hihihi100-laptop:~$ ls ~/.polipo/
ls: cannot access /home/hihihi100/.polipo/: No such file or directory
hihihi100@hihihi100-laptop:~$
```I used the webpage, the IP's are definitively different

Do u also use vidalia or tork?

---

### Post by mkvnmtr on 2010-03-28
It looks to me like vidalia will only be required if you want to use another browser. I downloaded it but it seems to conflict with torbutton. The other I am not familar with.
I would assume that the question about spanish was for me. Although I was a native englich speaker I have lived in Mexico a long time so yos I speak spanish. Sometimes I have trouble in both languages expressing myself. That just because I am old and befuddled.

---

### Post by greenhat.hackers on 2011-09-16
Can any one please tell me how to configure polipo in a server and how can i access it client machine.

---

### Post by josephmills on 2011-09-16
Open 
```
gksudo gedit /etc/apt/sources.list
```Scroll to the bottom and ADD
```
deb     http://deb.torproject.org/torproject.org <DISTRIBUTION> main
``` where you put the codename of your distribution (i.e. lucid, maverick,natty or whatever it is) in place of <DISTRIBUTION>.  
Save then exit 



Then add the gpg key used to sign the packages by running the following commands at your command prompt: 

```
gpg --keyserver keys.gnupg.net --recv 886DDD89 gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -  
```Now refresh your sources and install Tor by running the following commands  at your command prompt: 

```
sudo apt-get update 
```
then 
 ```
sudo apt-get install tor tor-geoipdb
```
Then 

```
sudo apt-get install sysv-rc-conf
```then open it 
```
sudo sysv-rc-conf
```scroll down to tor 
[IMG]http://img836.imageshack.us/img836/3404/sysv.png[/IMG]

and use the space bar to remove the x that are in the space 



[IMG]http://img443.imageshack.us/img443/4040/sysv1wmdbez.png[/IMG]



press q to quit 

reboot 

then 

```
sudo apt-get install vidalia
```[IMG]http://img441.imageshack.us/img441/8715/vidaj.png[/IMG]
[IMG]http://img835.imageshack.us/img835/1907/vida1.png[/IMG]


then start vidalia 
[IMG]http://img28.imageshack.us/img28/8238/vida3.png[/IMG]



Hope this helps

---

