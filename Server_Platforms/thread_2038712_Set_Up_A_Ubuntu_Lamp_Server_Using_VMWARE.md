---
title: "Set Up A Ubuntu Lamp Server Using VMWARE"
date: 2012-08-07
forum: Server Platforms
---

### Post by neodare on 2012-08-07
***********************************
Thanks ....the below post is old. i started a new install .check the post [http://ubuntuforums.org/showpost.php?p=12160125&postcount=9]("http://ubuntuforums.org/showpost.php?p=12160125&postcount=9")
************************************************


hi ,, 

i was trying to setup a Ubuntu Server with LAMP stack IN Vm and i prefer to try this completely Offline means on a machien without internet... the VM is is NAT Mode anways

Tried to Install VM server using VM easy install method but cant run TaskSel from commandline successfully bcz it doesnt show a LAMP Package ...

Then tried a Fresh Install on VM and got LAMP Stack to choose while installtion and i Ubuntu Server has LAMP pack within the CD. 

Now i Have a Shell on ubuntu server and identified the IP Address using Ifconfig ..



but cant access the web server using that IP from the Host Machine but the ping works ...

```
eth0 interaddress 192.168.11.136 Bcast 192.168.11.255
```

how can i know the webserver is working ? i knw basic linux But by using GUI ...So please help me ... found lot of tutorials to setup LAMP In Ubuntu by the two steps
1. tasksel lampserver installtion 
2. install phpmyadmin 


But what to do with the shell

---

### Post by LHammonds on 2012-08-07
> **neodare said:**
> 
i was trying to setup a Ubuntu Server with LAMP stack IN Vm and i prefer to try this completely Offline means on a machien without internet... the VM is is NAT Mode anways

Are you saying that you have the network configured so that the VM (ubuntu) can access the outside world but nobody else can see it?  If that is the case, you won't be able to access the IP of that server from your PC.

LHammonds

---

### Post by neodare on 2012-08-07
> **LHammonds said:**
> Are you saying that you have the network configured so that the VM (ubuntu) can access the outside world but nobody else can see it?  If that is the case, you won't be able to access the IP of that server from your PC.

LHammonds


no no. sorry for my bad english ...

i can ping from host to guest and also back..so i guess i can get the webserver when i give the guest Ip in first post to browser.
but its not showing ... i can see web server started message when server machine boots . but cant see see any page in browser.

---

### Post by LHammonds on 2012-08-07
I have not installed Ubuntu with the LAMP option.  I tend to have MySQL as a stand-alone server and the apps connecting to it remotely.

When Apache is installed and the service started, it "should" have a default page that says "It works!" when you go to that IP address.

Since Ubuntu Server is not graphical, you cannot "open a web browser to test locally" but you can use the command "wget" to see what is returned from the local IP (or use localhost)

Example:
```
cd /tmp
wget http://localhost -o /tmp/wget.log
vi /tmp/index.html
vi /tmp/wget.log
```

It will save what is sent to the browser which is typically saved to index.html.  It should have "It works!" somewhere in there between the BODY tags.

If see the "It works!" text, then you know your issue is networking and getting your server to communicate outside of its own NIC.

If you cannot see "It works!" then you will want to see what is in the wget.log file to see if any messages in there can help you track down the problem with Apache.

This is a sample of the wget.log file on my MediaWiki server (which works just fine):
```

--2012-08-07 12:04:03--  http://localhost/
Resolving localhost (localhost)... 127.0.0.1
Connecting to localhost (localhost)|127.0.0.1|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://10.0.0.10/index.php/Main_Page [following]
--2012-08-07 12:04:04--  http://10.0.0.10/index.php/Main_Page
Connecting to 192.168.107.23:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

     0K .......... .                                            300M=0s

2012-08-07 12:04:05 (300 MB/s) - `index.html' saved [12190]
```

The 127.0.0.1 is the local loopback for the machine (localhost)
The 10.0.0.10 is the IP address of your NIC (this is just an example IP)

LHammonds

---

### Post by darkod on 2012-08-07
If there is no specific reason the VM network to be in NAT mode, switch it to Bridged.

That will remove the NAT translation.

Note that you might need to set static or dhcp address on the VM eth0 interface, depending how your network is configured. With Bridged mode it's the same as if the VM is physical machine plugged into the network. So, configure eth0 accordingly.

---

### Post by neodare on 2012-08-07
> **LHammonds said:**
> 
Example:
```
cd /tmp
wget http://localhost -o /tmp/wget.log
vi /tmp/index.html
vi /tmp/wget.log
```
LHammonds


thnx bro..it worked ... i can see the source code of index.html and also the wget.log shows a sucessfull output ..


but why imnt getting the webserver from the host machine ??? 

is it beacuse of NAT ??.. Im Using VMPlayer. But in another machine (ubuntu 12.4 desktop) i used  Bridged connection with a Specific IP and it works fine. So i feels its some problem with the NAT ... 

but still i can ping ??? is there any firewall restriction on ubuntu server by default ??

Tried the IFCONFIG and it still shows the output which i posted on the starting of this thread ...

---

### Post by darkod on 2012-08-08
> **neodare said:**
> thnx bro..it worked ... i can see the source code of index.html and also the wget.log shows a sucessfull output ..


but why imnt getting the webserver from the host machine ??? 

is it beacuse of NAT ??.. Im Using VMPlayer. But in another machine (ubuntu 12.4 desktop) i used  Bridged connection with a Specific IP and it works fine. So i feels its some problem with the NAT ... 

but still i can ping ??? is there any firewall restriction on ubuntu server by default ??

Tried the IFCONFIG and it still shows the output which i posted on the starting of this thread ...

I don't know if you missed my post #5, if you are only reading the emailed replies it's easy to miss since it shows only the first one. Visit the thread.

Yes, it is because of the NAT mode. I don't think all ports are translated between the two addresses, hence port 80 of one IP has no clue about port 80 of the other IP. The same happens in Virtual Box for example.

It should work fine in Bridged mode, give it a go.

---

### Post by neodare on 2012-08-08
> **darkod said:**
> I don't know if you missed my post #5, if you are only reading the emailed replies it's easy to miss since it shows only the first one. Visit the thread.

Yes, it is because of the NAT mode. I don't think all ports are translated between the two addresses, hence port 80 of one IP has no clue about port 80 of the other IP. The same happens in Virtual Box for example.

It should work fine in Bridged mode, give it a go.
thanx darkod...and sorry i forgt to reply u last time .
ur first reply didnt make anything clear to me . 
Ya it was the problem with NAT . thought its a problem with VM player so tried on Virtual Box also. I bridged and and give a ip and it worked on VMPlayer. 
now i saw ur second reply after i tried the same ....thanx its ok anyhow ..




Now another help ..

I tried to install GUI for an easy way eventhought server isnt meant for that .. 

installed ubuntu-desktop no recommends , ya got a GUI with No apps (ya its good) But NO TERMINAL OR SHUTDOWN BUTTON... hehe. 

Then i installed Gnome Core ..later i wasnt happy with GUI .. beacused i gt used with CI ... 

Tried to remove ALL THE GUI with the same commands that i used to INSTALL

Like sudo apt-get install gnome-core xorg
sudo apt-get remove gnome-core xorg 

but i think this is nt removing things completely as i can see these packages in using command predictions and also imnt getting HDD Space back .

so tried 
> sudo apt-get remove gnome* 
sudo apt-get remove ubuntu*

show list of package removing messages 
thought it will make My Server to the initail stage removing all installed packages except LAMP..

but still it shows 1.5gb where a fresh LAMP ubuntu server shows only 800-900mb..


any suggestions ..

---

### Post by neodare on 2012-08-09
Ok.... Leave all my prev dbts...

I just started a new install of ubuntu server. Now i need a basic GUI . What abt Gnome minimal without any applications ?

Shuld i try
```
apt-get install gnome-core
or 
apt-get install gnome-shell
```

so i can start from CI using startx??

---

### Post by LHammonds on 2012-08-09
What are you wanting a GUI on the server for?  It would be hard for anyone to recommend one GUI over another unless there is a specific requirement/need.

I know this is not a production server but if it were, you would not want any GUI at all.

Some people like to use webmin to administer their server via a web browser.

Another possible option would be to use [Zentyal]("http://www.zentyal.org/") instead...they have a low-spec GUI built-in.  I use Zentyal for a print server since it was so easy to setup and maintain (unlike handling all the base components themselves)

LHammonds

---

### Post by neodare on 2012-08-09
basically im not good in ubuntu commands as im a newbie .. So i prefer the GUI components so that i can tweak the things .. So i jst need a basic GUI for gettings all the system options rather than any office or multimedia applications ...Yes its for a Development server only and im runing all from a single desktop ...

---

### Post by LHammonds on 2012-08-10
Everyone has their own preferences based on their skills and thinking process.  I like command-line because it is extremely easy to document and duplicate.  Check my signature for a few links to threads which contain all my steps for setting up a server...all with the command-line.  The only graphical images are the flowcharts I made to give a better visual representation of what I want to accomplish.

Keep in mind that it may not be too easy to "remove" a GUI once it is installed.  So go ahead and play around with it on a test server but I recommend avoiding any GUI at all on a production server...so you'll eventually need to learn how to manage it without the GUI.

Since you are running it in VMware, you can install the base server and take a snapshot just before installing a GUI.  Then install a GUI, try it out and when ready to try a different one, revert to your last snapshot which will rewind your server to a state BEFORE it ever had a GUI...very fast, very efficient for testing.

With that in mind, here are a few options you can research and try out:

```
sudo apt-get install lubuntu-desktop
```Lubuntu is based on LXDE which is a fast and energy-efficient environment.  I have Lubuntu installed on some ancient IBM PCs that have 384 MB of RAM.  The system boots up and takes up only 108 MB!

```
sudo apt-get install xubuntu-desktop
```  Kubuntu is based on Xfce and like Lubuntu, it is meant to run efficiently using as few resources as possible.
 
```
sudo apt-get install kubuntu-desktop
``` Kubuntu is based on KDE.

I am not positive (e.g. have not tried) but you might be able to install all 3 at the same time and pick which one you want to use at login.

LHammonds

---

### Post by neodare on 2012-08-10
thanks LHammonds.. 
i was trying XFCE, LXDE by directly installing , rather than xubuntu, lubuntu...
lxde is good and i love it than XFCE4...

---

### Post by neodare on 2012-08-11
im closing this thread .....


thanks all once again

---

