---
title: "NEED HELP: How to configure apt and synaptic under proxy"
date: 2005-10-08
forum: Repositories &amp; Backports
---

### Post by sabya on 2005-10-08
i have installed Ubuntu 5.10 (Breezy Badger) in my PC. please tell me how can i configure apt-get and synaptic for installing and downloading repositories under proxy.

please tell me in simple steps, so that i can understand (i am new in Linux:???:  )

waiting for ur reply.

---

### Post by kubano on 2005-10-10
```
http_proxy=http://proxy.server.name:port/
export $http_proxy
```
Regards

---

### Post by lovingboth on 2005-10-11
This is an annoyance I've just had.

When I first installed Ubuntu on a PC that used a proxy server for its internet access, finding what's now System / Preferences / Network proxy was easy. I could ping happily between the various machines on the network.

However it took some screaming 'But WHY won't you work?!?' at Firefox before I discovered (via google, I think) that it has separate proxy settings (why??) at Edit / Preferences / General / Connection.

This week, I discover that, again for some unknown reason, Synaptic has its own menu item for proxy settings. I would tell you exactly where (the first item on the Settings menu, I think) but it is currently downloading lots of packages over a dial-up connection and won't let me access the menus...

Why a) everything does not use the settings entered System / Preferences / Network proxy and b) how many other programs do not do so, I do not know. 

But there should be something in big red letters telling you (and me) so.

Oh, I'm guessing that the magic recipe someone else has given needs to be typed at a terminal, possibly as the superuser. I may well be wrong, but it would have been helpful if it was clearer.

(Update: it's Synaptic's Settings / Preferences / Network menu item.)

---

### Post by dlai on 2006-02-15
yes i've been trying to find this general proxy for a while too... but I can't find it...

---

### Post by public_void on 2006-02-15
I'm behind a proxy as well. Have you editted the file /etc/apt/apt.conf, and add your proxy settings in there. If not heres how in the terminal

cd /etc/apt/ (Changes the directory to /etc/apt/)
cp /etc/apt/apt.conf /etc/apt/apt.conf_backup (Copies the file apt.conf to the same directory be renames it apt.conf_backup. This is incase you make a mistake, you don't have to do that command)
sudo gedit apt.conf (Opens apt.conf in a text editor and allows you to edit it)
Add the lines

```

ACQUIRE { 
http::proxy "http://[Username]:[Password]@[Address]:[Port]/" 
}
```

If you don't use a username and password then remove "[Username]:[Password]@". Once done, change the proxy server in Synaptic to "Direct connection to the internet". I don't know why but it worked for me.

This is the 3rd or 4th time I've posted this maybe they should add this somewhere like the Ubuntu Starter guide or something, somewhere easy to find.

---

### Post by pcrage69 on 2006-03-31
I have done what's posted above with no luck.  Any more ideas?

---

### Post by SgtDude on 2006-04-28
[QUOTE=dlai]yes i've been trying to find this general proxy for a while too... but I can't find it...[/QUOTE]

This might not be the answer you're looking for, but if you're in a position to fiddle with the layout of your network, you might consider setting up what's known as a "Transparent Proxy".  I won't get into the nitty gritty here (mainly because I've never actually set one up personally), but basically it's a combination of IPtables pulling NAT duty, and Squid running on a box acting as your default gateway.

What this does is allow you to configure all of your machines as if there was no proxy, but still get the proxy benefits.  The possible downside to this is that if you have machines or applications that don't cooperate with NAT well, you'll have to set up annother path for them.  But software that doesn't like NAT is increasingly uncommon these days.

---

### Post by geog_eric on 2006-05-03
I'm also a newbie to Ubuntu (not to Linux) and having trouble with proxy settings for Synaptic. I've figured out the following:

I've modified .bashrc to add **http_proxy** as described above. This allows me to run a Synaptic session via the command line, via "sudo synaptic" that will successfully get through the proxy server. Same holds for gnome-app-install. However, I still can't get Synaptic to see past the proxy server if I start it from the gnome GUI. I've added my proxy settings to Synaptic->Settings->Preferences->Network and the gnome System->Preferences->Network Proxy--I still get a "proxy authentication" error in Synaptic and from the Add/Remove Applications (gnome-app-install).

My goal was to install Ubuntu (Dapper Beta) without opening a terminal window. I didn't succeed.

Anyone have further advise? Particularly with successfully setting up a proxy server through the gnome GUI?

---

### Post by shai1 on 2006-06-08
I'm running dapper and have been able to get synaptic running using 
sudo synaptic 
having configured bashrc with my proxy settings but I still can't get it to work through a proxy if I start it from the system menu. 

I dont know if this is a bug but if there's anyone working on Ubunt here then this needs a fix now

---

### Post by kettek on 2006-06-15
I have had tons of proxy issues, being behind the corporate firewall and all.  The last thing I tried was in System > Preferences > Network Proxy.  We have a proxy script that we usually use, but ubuntu no likey that.  So, in Network Proxy, I put the proxy info into each of the provided fields instead.  Voila!  It worked.

Something else I've noticed...I've seen the entry in /etc/apt/apt.conf listed two different ways.  Don't know how much difference it makes, but I've seen it as:

Acquire::http::Proxy "http://blah.blah.blah:8080";

That's how it looks in Dapper.  I've also seen it kinda like this:

ACQUIRE {
  http_proxy='http://blah.blah.blah:8080";
}

I'd be curious to see if using one or the other makes any difference.

---

### Post by Seer on 2006-06-29
I have no idea how linux can be expected to be taken seriously when the basics like this are not addressed. It's absolutely appalling to think that you need to configure the proxy for each and every application.. but especially those that are core components of the distrubution i.e. Synaptic!

Windows you configure your proxy (and all other internet settings) and every app takes it's settings from there (apart from badly made ones!)

---

### Post by mitrellim on 2006-06-29
I am under a proxy at school and use an outside program to make the proxy work. It is very easy. I have attached the necessary program. Read the instructions in the file instructions.txt

Tim Miller

---

### Post by BoomAM on 2006-07-27
My apt.conf file is setup as follows:
Code:

ACQUIRE { http::proxy "http://[Administrator]:[Change_Me]@[192.168.3.253]:[80]/" }

But it doesnt work from either the command line or the menu items.

I just keeping getting 407 errors (proxy requires authentication).
Ideas?

---

### Post by digvijay on 2007-04-08
have u used NTLM it can also be used to tunnel proxy's 
if no then i will send it as an attachment :guitar:

---

### Post by digvijay on 2007-04-08
> **public_void said:**
> I'm behind a proxy as well. Have you editted the file /etc/apt/apt.conf, and add your proxy settings in there. If not heres how in the terminal

cd /etc/apt/ (Changes the directory to /etc/apt/)
cp /etc/apt/apt.conf /etc/apt/apt.conf_backup (Copies the file apt.conf to the same directory be renames it apt.conf_backup. This is incase you make a mistake, you don't have to do that command)
sudo gedit apt.conf (Opens apt.conf in a text editor and allows you to edit it)
Add the lines

```

ACQUIRE { 
http::proxy "http://[Username]:[Password]@[Address]:[Port]/" 
}
```

If you don't use a username and password then remove "[Username]:[Password]@". Once done, change the proxy server in Synaptic to "Direct connection to the internet". I don't know why but it worked for me.

This is the 3rd or 4th time I've posted this maybe they should add this somewhere like the Ubuntu Starter guide or something, somewhere easy to find.

but what should be the setting of synaptic in menu
settings>preferences
network tab 
manual proxy 
HTTP proxy :   ?????            port  : as return in your code
FTP proxy :  ??????              port: as return in u r code

---

### Post by jorno on 2007-09-10
I don't know if anyone still has this problem, but I found my solution in another post.

The steps mentioned here earlier are good and all, BUT if those of  you who's got this problem is in a Windows environment with a Microsoft ISA Proxy that need authentication, this is the solution that worked for me:

You need to install NTLMAPS.

[http://packages.ubuntu.com/feisty/web/ntlmaps](http://packages.ubuntu.com/feisty/web/ntlmaps)
* Go there, and download, either from within Firefox (if you manage to get Proxy working with Firefox - I did, but not apt-get or Synaptics or anything else).
* Download the package for ntlmaps (this is for Ubuntu Feisty)
* Start a terminal, find your downloaded package, and type:
*sudo dpkg -i ntlmaps_0.9.9.0.1-6_all.deb*
This should guide you trough the installation of the package...

BUT, my problems didn't stop there!
After, I had to edit /etc/ntlmaps/server.cfg manually.
( *sudo vim /etc /ntlmaps/server.cfg* )
Then I saw that the config-file was formatted with DOS (not UNIX), so I had to tell vim to convert it to UNIX-format. Do this in vim:
*:set fileformat=unix*
*:wq*
This should convert the file, and save it.
I also had to change some of the options:
Under the [CLIENT_HEADER] section, I had to comment out the first Accept and User-Agent part (Windows 98), and then uncomment the next part (Windows 2000 emulation).
Then I filled in "NT_HOSTNAME" (remembered what PC number this workstation had in Windows), and "NT_DOMAIN").

After those changes, restart ntlmaps:
*/etc/init.d/ntlmaps restart*

And point all your proxy-settings to: [http://127.0.0.1:5865](http://127.0.0.1:5865)

Make a file: */etc/apt/apt.conf*
Acquire::http::Proxy "http://127.0.0.1:5865";

And then try "*apt-get update*".

You could also insert this into:
System -> Preferences -> Network Proxy

And in Synaptics:
System -> Administration -> Synaptics -> Settings -> Preferences -> Network:
Manual proxy configuration:

127.0.0.1 port 5865 (no authentication)


This should do the trick! It did for me.. Please ask if there is something not clear yet, or if I should correct any of this. (Sorry, English is not my native tongue).

---

### Post by crazysexycool on 2007-09-27
Hi guys i had the same problem with proxy settings my solution 

change file in apt which is apt.conf

put Acquire::http:: "http://domain%5Cuserid:password@proxy:port"

what i also noticed after this is that i need to change my synaptic settings to manual proxy config using the same details as above for user id and password 

and my network proxy i changed to direct internet connection and its working why i have no idea.

---

### Post by kaumiryuu on 2008-08-20
My solution for APT

Create file PROXY in /etc/apt/apt.conf.d/

Add this

Acquire::http::Proxy "http://[username]:[password]@[proxyserver]:[port]";

OR

Acquire::http::Proxy "http://[proxyserver]:[port]";

And try.

Regards

---

### Post by LukaszSJHS on 2009-08-03
I had a problem getting past our proxy server on Ubuntu Server 8.04.
The solution was that I had to ask permission to bypass the proxy.  Our hypothesize was that Linux cannot authenticate against this proxy because the proxy required a Windows authentication.   Perhaps there is a method of authentication, but a username and password in the conf.apt file was insufficient.

---

### Post by bazzieb on 2011-01-27
Hi jorno

Thanks, your how to really helped me. 

Regards

---

### Post by bit mad on 2011-05-04
And it's still a problem in Natty 11.04! :o

Just been playing with 11.04 from a USB stick, pleasantly surprised that Unity isn't as bad as the one-window-at-a-time UNR, glad I've tried it. Even the window controls on the wrong side and the new scroll bar doo-dads aren't too bad.

But.... having entered the Network Proxy settings (including Authentication name and password), Firefox still asks for a proxy login each time it's fired up. And the settings aren't added to **/etc/apt/apt.conf** with the Username and Password, so Ubuntu Software Centre didn't work -  I've had to manually gedit *(YES, fire up a terminal in the first hour with 11.04 - newbie-friendliness fail!)* as something like this :

Terminal command: **sudo gedit /etc/apt/apt.conf**
```
Acquire::http::proxy "http://JohnDoe:MyPassword@192.168.167.159:8080/";
Acquire::ftp::proxy "ftp://JohnDoe:MyPassword@192.168.167.159:8080/";
Acquire::https::proxy "https://JohnDoe:MyPassword@192.168.167.159:8080/";
```*(names changed to protect my innocence)*

The Software Centre then actually works!

Apart from that, looking good! :D

(except for trying to play the first likely looking interesting game Critical Mass which made everything all seize up, I'm too newbie to know how to kill a process from a ctrl-alt-F1 terminal, I ended up having to reboot but the USB key was trashed after that, so I've had to redo the USB key in LiLi all over again :P )

---

### Post by dabbish on 2011-12-05
I am behind a NTML proxy and I installed CNTLM and followed this tutorial:

[http://www.denoq.com/2011/10/ubuntu-ntlm-authentication-on-windows-domain/](http://www.denoq.com/2011/10/ubuntu-ntlm-authentication-on-windows-domain/)

Then I could use commands like wget. Although after adding localhost:8080 in the Ubuntu 11.04 network proxy settings I could still not get apt-get to work. To get that to work as well I had to do what bit mad suggested:

```

Acquire::http::proxy "http://JohnDoe:MyPassword@localhost:8080/";
Acquire::ftp::proxy "ftp://JohnDoe:MyPassword@localhost:8080/";
Acquire::https::proxy "https://JohnDoe:MyPassword@localhost:8080/";

```

I hope that helps someone.

---

