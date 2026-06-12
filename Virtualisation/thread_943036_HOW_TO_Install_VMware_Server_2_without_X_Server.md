---
title: "HOW TO: Install VMware Server 2 without X Server"
date: 2008-10-09
forum: Virtualisation
---

### Post by lazyart on 2008-10-09
With VMWare Server 2 using a web based console, there is no need to even install X on your server.  The result is more memory and processing power available for your VMs.  This was tested on Hardy Heron. **Note: This method does not install a sound card in the VM.

[SIZE="5"]**Register.**[/SIZE]
Visit [http://www.vmware.com/go/getserver]("http://www.vmware.com/go/getserver"). Create an account and get your serial number for the installation.  Print your registration code as you will need it later.  Don't download it yet.

**[SIZE="5"]Start with a minimal Ubuntu Server install.[/SIZE]** 
You won't need to add any additional server roles.

[SIZE="5"]**Add additional packages.**[/SIZE] 
After you have booted into the console, enter```
sudo apt-get install psmisc libxrender1 libxt6 build-essentials linux-headers-`uname -r` links2 openssh-server
```

[SIZE="5"]**Download VMWare Server 2.**[/SIZE] 
Unfortunately there seems to be no way to use WGET to get the package from the command line, so we'll roll back the clock to the early 80's and browse the web in text mode!```
cd /tmp
sudo links2 http://www.vmware.com/go/getserver
```Use the up and down arrows to move between fields. Log in with your email address and password you created on your first visit  (if you mistyped the URL, hit G and re-enter). Highlight [Submit] and hit Enter to get to the download page.  Your serial numbers should show again... scribble them down if you haven't already.  Use the down arrows to find the 32 bit or 64 bit TAR image you need.  Hit Enter and the download will proceed.

[SIZE="5"]**Stretch your legs.**[/SIZE] 
The toughest part is behind you.  The download is 500MB.  When the download is complete, hit Q to exit links2.

[SIZE="5"]**Extract the tarball.**[/SIZE] 
```
sudo tar -xvzf VMware*
```

[SIZE="5"]**Install and configure VMware Server 2.**[/SIZE]
```
vmware-server-distrib/vmware-install.pl
```Blast through the defaults.  After you have configured networking, be sure to set yourself as the administrator.  Finally, when entering the serial number DO IT IN CAPS or you'll have to enter it all over again.

[SIZE="5"]**Set a static address.**[/SIZE] 
You'll probably want to set your server to a static IP address.```
sudo nano /etc/network/interfaces
```Here is a sample configuration with the server at 192.168.1.19, submask 255.255.255.0 and gateway of 192.168.1.1```
iface eth0 inet static
	address 192.168.1.19
	netmask 255.255.255.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
```
Now, restart networking for the changes to take effect```
sudo /etc/init.d/networking restart
```

[SIZE="5"]**Clean up!**[/SIZE] 
We've eaten up over a gig in space in the /tmp directory which we won't need anymore.```
cd /tmp
sudo rm VM*
sudo rm vm* -R
```

[SIZE="5"]**Test.**[/SIZE] 
Go to another machine on your network and browse to [https://SERVER_IP_ADDRESS:8333](https://SERVER_IP_ADDRESS:8333). Accept the certificate (you'll likely have to make an exception for it) and you'll see the VMWare web console!  You can create a VM and install a graphical OS without having a GUI on the server!

SSH was included to manage the server.  If you prefer ftp, install your preferred ftp server to add .iso images, or create a datastore on another machine that holds those files for you.

---

### Post by holepunch on 2008-10-30
First, thanks for such a thorough post.

Now to business; I did all that on to Ubuntu Server 8.04.1 i386 then went to my main machine with a GUI and tapped in the address and was able to set up some virtual machines.  I was well impressed until I rebooted the server that I had installed VMware Server on to find that I could no longer access it from my main machine.

When I try to access it I get a blank page with the title 'Loading'.  I ssh'd the server and tried restarting 'vmware' to be told:

'Failed to launch VMware Web Access: unable to find a graphical web browser.'

Any clues?

FYI: I ran 'sudo apt-get install firefox' on the server to see if that would make it any happier but it now says 'Error: no display specified'.

---

### Post by lazyart on 2008-11-05
the command 'vmware' launches the web client, which of course won't work because you didnt have a browser, and of course again because there is no X display.

I would run thru the installation of vmware again as it seems like it's not running.  Checking the logs might also give a hint.  I honestly didnt run into this issue.

---

### Post by mad-kow on 2008-11-07
First of all thank you for this great post.

On my machine i didn't need to install that many packages. Trying to install links2 even ended up in a X Server installation - which i canceled of course. Therefore i used another machine to do the download and copied the tar file with scp.

This is what i installed:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

And im not even sure if they are really needed, as the installation didn't compile anything on my maschine (Ubuntu Server 8.04.1) with the lastest vmware release (VMware-server-2.0.0-122956.i386.tar).

---

### Post by Zoree on 2008-11-07
Can someone please tell me why i cant connect with VMWare Infrastructure Client?

When i try i get this message?

VMware Infrastructure Client could not establish the initial connection with server "10.0.0.130".

Details: A connection failure occurred.

---

### Post by omega_drh on 2008-12-11
> **Zoree said:**
> Can someone please tell me why i cant connect with VMWare Infrastructure Client?

When i try i get this message?

VMware Infrastructure Client could not establish the initial connection with server "10.0.0.130".

Details: A connection failure occurred.

Apparently VIClient tries to connect to 443/tcp by default. I recognized this as the default port for https, but vmware-server2 runs https on 8333 by default. If you enter '10.0.0.130:8333' in the virtual infrastructure client connection dialog, it'll connect! Enjoy!

---

