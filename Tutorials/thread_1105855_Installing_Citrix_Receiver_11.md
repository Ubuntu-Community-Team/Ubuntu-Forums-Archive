---
title: "Installing Citrix Receiver 11"
date: 2009-03-25
forum: Tutorials
---

### Post by rosv on 2009-03-25
Hi,
Installing Citrix Receiver isn't rocket science, but considering it took me a while to get it working I figured it might be useful.

By the way. Citrix Receiver is the new name for Citrix ICA client. Renaming products, without changing too much of it's code, is one of Citrix favorite things to do.

Anyway, let's install.

1. Download the client: [http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755](http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755)

2. Unpack the tar.gz: tar xfvz linuxx86-11.0.140395.tar.gz

3. Execute the install script: sudo ./setupwfc

4. Accept the default options (or whatever seems most appropriate)

5. Install openmotif: sudo apt-get install libmotif3

6. Run ldd to check for dependecy issues:ldd /usr/lib/ICAClient/wfcmgr
	linux-gate.so.1 =>  (0xb7fa9000)
	libXm.so.4 => not found
	libXp.so.6 => /usr/lib/libXp.so.6 (0xb7f92000)
	libXpm.so.4 => /usr/lib/libXpm.so.4 (0xb7f81000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb7f79000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb7f61000)
	libXmu.so.6 => /usr/lib/libXmu.so.6 (0xb7f4b000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f47000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f2f000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7ddf000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0xb7d8e000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb7ca7000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c99000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb7c96000)
	/lib/ld-linux.so.2 (0xb7faa000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb7c93000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb7c7b000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7c76000)

As you can see, libXm.so.4 is missing and the executable wont run.

7. To solve this problem, create a sybolic link between for ldd /usr/lib/ICAClient/wfcmgr: sudo ln -s /usr/lib/libXm.so.3 /usr/lib/libXm.so.4

8. Do an other ldd dependency check:
ldd /usr/lib/ICAClient/wfcmgr
	linux-gate.so.1 =>  (0xb7f80000)
	libXm.so.4 => /usr/lib/libXm.so.4 (0xb7d31000)
	libXp.so.6 => /usr/lib/libXp.so.6 (0xb7d29000)
	libXpm.so.4 => /usr/lib/libXpm.so.4 (0xb7d19000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb7d10000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb7cf8000)
	libXmu.so.6 => /usr/lib/libXmu.so.6 (0xb7ce2000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7cde000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7cc6000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b77000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0xb7b25000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb7a3e000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb7a30000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb7a2d000)
	/lib/ld-linux.so.2 (0xb7f81000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb7a2b000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb7a12000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7a0d000)

The Citrix Receiver client should not able to run. On my ubuntu 8.04, the Citrix receiver client is found under: Ubuntu / Internet / Citrix receiver client.

---

### Post by sharksandwich79 on 2009-03-27
That worked perfectly for me, thank you!=D>

---

### Post by pdowling on 2009-03-29
So glad I found this thread.  Definitely saved me some time - thanks!

---

### Post by talz13 on 2009-04-02
I just tried this, but I"m running 64 bit hardy, and I don't have a libXm.so.3 anything under my /usr/lib32 folder. I do have one under my /usr/lib like in your example, but after linking with:```
sudo ln -s /usr/lib/libXm.so.3 /usr/lib/libXm.so.4
``` it still results in:```
jeff@server:~/apps/citrix/linuxx86$ ldd /home/jeff/apps/citrix/linuxx86/wfcmgr 	linux-gate.so.1 =>  (0xffffe000)
	libXm.so.4 => not found
	libXp.so.6 => /usr/lib32/libXp.so.6 (0xf7f77000)
	libXpm.so.4 => /usr/lib32/libXpm.so.4 (0xf7f66000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7f5e000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7f46000)
	libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf7f30000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7f2c000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7f14000)
	libc.so.6 => /lib32/libc.so.6 (0xf7dc4000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7d73000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7c8c000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7c7e000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7c7b000)
	/lib/ld-linux.so.2 (0xf7f98000)
	libxcb-xlib.so.0 => /usr/lib32/libxcb-xlib.so.0 (0xf7c78000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf7c60000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7c5b000)
```

---

### Post by talz13 on 2009-04-03
I got the problem with ubuntu 64 resolved by following the instructions in this post at the citrix forums by Mark Syms:

[http://forums.citrix.com/thread.jspa?messageID=1371285](http://forums.citrix.com/thread.jspa?messageID=1371285)

> On 64 bit Ubuntu you can do the following to get the 32 bit version of the Open Motif libraries installed.

mkdir motif
cd motif
wget [http://ftp.ubuntu.com/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-2_i386.deb](http://ftp.ubuntu.com/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-2_i386.deb)
dpkg -x libmotif3_2.2.3-2_i386.deb .
sudo cp -r usr/lib/* /usr/lib32/

(For client V11)
sudo ln -s /usr/lib32/libXm.so.3 /usr/lib32/libXm.so.4

So, in detail, we pull the 32 bit version of the libmotif package from the Ubuntu store. The version number may differ so run

apt-cache show libmotif3

Which will show you the details of the 64 bit version of libmotif (assuming you have the multiverse repository available). In the middle of this there is a filename something like

Filename: pool/multiverse/o/openmotif/libmotif3_2.2.3-2_amd64.deb

Which you can see is the same as the bit above with the i386 changed to amd64.

We then extract the contents of the package into a temporary directory and then copy the libraries into the 32 bit library area in the machine.

Hope that helps people,

Mark.

---

### Post by KarelZ on 2009-04-06
Thanks rosv, this helped me out for running the Citrix Client under Ubuntu Netbook Remix.

---

### Post by LeoPerezC on 2009-04-21
Excelent help. I really apreciate it.
Thanks
Leo

---

### Post by bpgasguy on 2009-04-24
thanks for the info citrix is up and runnin on 9.04

---

### Post by del13r on 2009-04-27
thank you. worked perfect after your advice.

---

### Post by KennyUnger on 2009-04-28
Thanks a lot! This helped me get the Citrix Receiver (why do they insist on constantly renaming everything) working on Ubuntu 9.04! I did not know about the "ldd" command before.

---

### Post by Jimmmac1 on 2009-05-07
Good morning

Two things from this post that I could use some help on. 

1. I read on another post that for Receiver 11 to work correctly, you have to uninstall the old libmotif.  Is this true?

2.  My citrix is working and I am able to log into my work computer.  But when I rdp to my workstation, the mouse does not work, or more accurately track correctly.  

I had it working with 8.10, but 9.04 works, but not correctly. Does anyone have any ideas as to how to solve this problem?  Thanks for the help.

Jim

---

### Post by Jam3s0n on 2009-05-19
Thank you for the info

---

### Post by genesis2seven on 2009-05-21
Everything installed fine and I can launch the Receiver client from my applications menu just fine however, when I go to my company's site and click login the window for my desktop doesn't launch. I check my plugins directory for firefox and the Citrix plugin is there. Any help?

---

### Post by alexcckll on 2009-06-12
Hi folks, 

THinking just about my work - I can see where this is a critical requirement as more companies (esp enterprises) go towards Citrix for most of their platform. (Citrix/Softgrid allows more mainframe-like running for Windows apps with apps hermetically sealed off from the OS - less DLL hell).

I know the client is closed-source, but might this be something to consider for UNR as well?

---

### Post by sunirbmag on 2009-06-12
Hi all,

does anybody know how to get write access to the files on my computer from the client?

Thanks,
Sunirb

---

### Post by ssnowden on 2009-06-15
This worked for my AMD 64-bit. Thanks.

---

### Post by lesmyer on 2009-06-19
> **rosv said:**
>  
5. Install openmotif: sudo apt-get install libmotif3

 
I installed per Citrix Admin Guide instructions in 9.04. Did not have to deal with anything (such as openmotif, dependencies) after step 4 to connect to my company's server except for the usual code 61 error which is solved by obtaining and putting the appropriate cert in the [SIZE=2]usr/lib/ICAClient/Keystore/cacerts/ [/SIZE]directory as root. 
 
Here is the Citrix Receiver for Linux Admin guide:
 
[[COLOR=red]http://support.citrix.com/servlet/KbServlet/download/19362-102-19735/Citrix-Receiver-for-Linux-Administrators-Guide.pdf[/COLOR]]("http://support.citrix.com/servlet/KbServlet/download/19362-102-19735/Citrix-Receiver-for-Linux-Administrators-Guide.pdf")
 
LM

---

### Post by grimeywelsh on 2009-07-08
Thanks you for this.  This post will keep me Windows free for another semester at DeVry online!

---

### Post by alexcckll on 2009-07-09
I have to ask - why isn't this simply in a Partner repository?  Just an apt-get away, or rolled out as part of the default?

---

### Post by johnp645 on 2009-08-03
Thank you for your help! Works great.

---

### Post by dmflad on 2009-09-12
Running 9.04 32-bit and had installed Citrix Receiver 11 per Citrix manual but had problem with libXm.so.4 dependency.  Linking to libXm.so.3 did not help until I did: ```
sudo apt-get install libmotif3
```
Now Citrix works.

---

### Post by alexcckll on 2009-09-18
But why the heck should all this be needed?

Surely all Citrix need to do is approach Canonical - and have the full support and all dependencies identified - and get the full ICA client into the Partner repository?

I would like to be able to type sudo apt-get install citrix-receiver - and let the package manager handle it all for me...

---

### Post by joe110010 on 2009-09-30
[SIZE=2]Hi, this generally worked for me - thanks! [/SIZE]

[SIZE=2]I had a problem with error code 61, which took a while to fix. My company uses COMODO. I saw there were like 5 Comodo certificates already in the cert folder, so I was getting frustrated it wouldn't work, because I thought well, one of them must apply. Eventually I went to the Comodo website and found one that matched the exact name of the Comodo referenced in the error message I was getting. It was something like Comodo High Assurance (I'm not at home now), which actually was designated an intermediate certificate, not a root certificate like was emphasized in some online guides (?). Downloading and putting it in the cert folder made it work. [/SIZE]

[SIZE=2]Being new, can someone explain how or why you would know to install libmotif3 - i.e., what is the openmotif program? I couldn't tell where that came from.[/SIZE]

---

### Post by rockprincess on 2009-11-23
this works great, but my problem is that, once i go to my company's website and log in, it's STILL starts the Java web-based version JICA97....why does it not launch the citrix client that I just installed on my computer?

the java version is a pain in the ****... :(

any ideas?!

---

### Post by Adamas Pondera on 2009-12-03
Bravo!

---

### Post by likerice on 2010-02-21
Worked beautifully on 9.10 (Karmic) / Gnome 2.28.1 / 2.6.31-20-generic kernel.

Now I can work from home without using the wife's Mac. Thanks!

---

### Post by 98cwitr on 2010-03-23
Back from the dead...installed today on 10.04. Installed fine and all dependencies are in, but when I execute RDP from the web browser, it will open and display my login prompt, the mouse is off about 10-20 pixels for input. Any ideas? Really annoying.

---

### Post by geo_shonkylogic on 2010-03-24
Yes, it works in Lucid, but you also need to install the Equifax Secure Global eBusiness Certificate.

Quick instructions: Download the certificate from [https://www.geotrust.com/resources/root-certificates/index.html](https://www.geotrust.com/resources/root-certificates/index.html)

1) Rename your downloaded file from .cer to .crt

mv Equifax_Secure_Global_eBusiness_CA-1.cer Equifax_Secure_Global_eBusiness_CA-1.crt

2) copy the certificate into /usr/lib/ICAClient/keystore/cacerts

you will need to sudo to do this

sudo cp Equifax_Secure_Global_eBusiness_CA-1.crt /usr/lib/ICAClient/keystore/cacerts

And it should work....

---

### Post by 98cwitr on 2010-03-24
nice freakin first post dude haha :P But, just my luck, didnt make a diff :(

---

### Post by geo_shonkylogic on 2010-03-27
> **98cwitr said:**
> nice freakin first post dude haha :P But, just my luck, didnt make a diff :(

Whoops.. You will **also** need to download the Equifax_Secure_Certificate_Authority_DER.cer file from the site above.  Rename it to a .crt file and copy it to the same directory and Citrix client should then work ok on Lucid.

---

### Post by tomeq on 2010-04-02
> **geo_shonkylogic said:**
> Whoops.. You will **also** need to download the Equifax_Secure_Certificate_Authority_DER.cer file from the site above.  Rename it to a .crt file and copy it to the same directory and Citrix client should then work ok on Lucid.

Hmm, what for? To get rid of displaced mouse pointer? C'mon. 

I have the same issue too...

---

### Post by shof2k on 2010-05-30
Worked perfectly.  Thank you for a clear, well written guide.

Peace

---

### Post by burnhero on 2010-08-18
Sorry to get off topic, but I've been looking for an answer for quite some time.  There is an annoying overlay in the middle of the screen when having Citrix applications launched.  The overlay is a gray dot with a white center.  You can see it in the screen shot.

This overlay gets more and more intense the more Citrix apps I have running.  Is there any way to get rid of this?  I am going to look through the admin guide again to see if there is an answer hiding.

---

### Post by alynx on 2010-08-20
This guide is perfect :p

---

### Post by DogFace on 2010-10-12
Thank you for the instructions.  I was able to get the Citrix client up and running with relatively little hassle.

I am having one significant problem, though.  When I run an application remotely via Citrix, I am unable to display the application's window on my screen.  I know the application is running because I can see the tab for it on the bar at the bottom of my screen.  However, when I try to display the window, the screen refreshes but all I can see is the image that was on my screen before I maximized the application window.  This appears to be a graphics/screen drawing problem.  Any thoughts on how to fix it?

---

### Post by sonofzell on 2011-01-14
Wow - I've been struggling with this for weeks.  Thanks a million!

---

### Post by BigCityCat on 2011-01-16
Okay I finally got it to work. Anyone who is getting the ssl error. Here is the link where I found the info to fix this problem.

[http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex](http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex)

I am posting the instructions here so if the website stops hosting it. It won't get lost.

> My main problem is the package provided by Citrix requires extra steps to get it working, specifically adding a root certificate to a certain directory so that you can avoid this error:

[QUOTE]You have chosen not to trust "Thawte Premium Server CA", 

the issuer of the server's security certificate (SSL error 61).

linux citrix client ssl error 61 certificate

So getting the client software and installing it is fairly simple. But many people have run into this SSL error 61. The fix for this is to get the certificate file and put it in the right directory for the citrix client to find when you log onto citrix and run your citrix apps.

I&#8217;ve created a very simple bash script to perform this task. You can download it here:

[http://geekpete.com/blog/code/fix_citrix_cert_v0.2.sh](http://geekpete.com/blog/code/fix_citrix_cert_v0.2.sh)

Otherwise, these are the steps you can perform manually that I&#8217;ve found this to work with Ubuntu 8.10.

    Download [https://www.verisign.com/support/thawte-roots.zip](https://www.verisign.com/support/thawte-roots.zip)
    Extract ThawtePremiumServerCA.cer from the &#8220;Thawte SSLWeb Server Roots&#8221; directory inside the zip.
    Copy the cert file to /usr/lib/ICAClient/keystore/cacerts and make sure you rename it to .crt

Note: If you install the citrix client as your local user (rather than installing as root) then your certs directory will be /home/yourusername/ICAClient/linuxx86/keystore/cacerts so your ThawtePremiumServerCA.crt should go there instead.[/QUOTE]

---

### Post by SigmaKS on 2011-03-17
Thank you so much for these tips. I was finally able to get the necessary programs installed after I figured out that my file structure was slightly different that listed in the instructions. I am a new Ubuntu 10.10 netbook remix user and this was the one thing that was really holding my productivity back. Now I am able to use this little netbook to login to check work e-mail and even get an iSeries session up. Yay Linux!

---

### Post by BigCityCat on 2011-04-05
I had to reinstall and the second time I had this problem and the following solution worked for me.

> Quote:
Originally Posted by sunyan1999 View Post
I followed the procedures laid out here. First installed the libs and then extracted the linuxx86.tar.gz. But when I run ./setupwfc, I got the following:
/tmp/citrix/en.linuxx86/linuxx86/hinst: 236: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 237: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 238: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 239: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4011: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4027: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4043: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4043: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4043: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4043: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found


Can anybody help? I have been able to install Citrix 10.6 on another computer with Gutsy 32bit without any problem. Thanks.

To get around this I just bypassed their echo_cmd command. If you edit setupwfc and look at line # 546 you should see:

ECHO_CMD=${PLATFORM_PACKAGE_DIR}/$TR_FILE export ECHO_CMD

Comment that out with a leading "#" and put this in it's place:

ECHO_CMD=echo

Seems to be working for me

---

### Post by Zbor on 2011-04-12
After running ```
$ sudo cp -r /usr/lib/* /usr/lib32/
```I get 
```
$ ldd /usr/lib/ICAClient/wfcmgr
    linux-gate.so.1 =>  (0xf771b000)
    libXm.so.4 => not found
    libXp.so.6 => not found
    libXpm.so.4 => not found
    libSM.so.6 => not found
    libICE.so.6 => not found
    libXmu.so.6 => not found
    libXinerama.so.1 => not found
    libdl.so.2 => /lib32/libdl.so.2 (0xf76f2000)
    libpthread.so.0 => /lib32/libpthread.so.0 (0xf76d9000)
    libc.so.6 => /lib32/libc.so.6 (0xf757e000)
    /lib/ld-linux.so.2 (0xf771c000)
    libXt.so.6 => not found
    libX11.so.6 => not found
```
What did I miss?

Everything looked fine before that
```
$ ldd /usr/lib/ICAClient/wfcmgr    linux-gate.so.1 =>  (0xf77cc000)
    libXm.so.4 => not found
    libXp.so.6 => /usr/lib32/libXp.so.6 (0xf77a0000)
    libXpm.so.4 => /usr/lib32/libXpm.so.4 (0xf778e000)
    libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7785000)
    libICE.so.6 => /usr/lib32/libICE.so.6 (0xf776c000)
    libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf7755000)
    libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf7751000)
    libdl.so.2 => /lib32/libdl.so.2 (0xf774d000)
    libpthread.so.0 => /lib32/libpthread.so.0 (0xf7733000)
    libc.so.6 => /lib32/libc.so.6 (0xf75d8000)
    libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7585000)
    libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7468000)
    libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7458000)
    libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7454000)
    libuuid.so.1 => /lib32/libuuid.so.1 (0xf744e000)
    /lib/ld-linux.so.2 (0xf77cd000)
    libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf7434000)
    libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf742e000)
$ sudo ln -s /usr/lib32/libXm.so.3 /usr/lib32/libXm.so.4
$ ldd /usr/lib/ICAClient/wfcmgr    linux-gate.so.1 =>  (0xf777c000)
    libXm.so.4 => not found
    libXp.so.6 => /usr/lib32/libXp.so.6 (0xf7750000)
    libXpm.so.4 => /usr/lib32/libXpm.so.4 (0xf773e000)
    libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7735000)
    libICE.so.6 => /usr/lib32/libICE.so.6 (0xf771c000)
    libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf7705000)
    libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf7701000)
    libdl.so.2 => /lib32/libdl.so.2 (0xf76fd000)
    libpthread.so.0 => /lib32/libpthread.so.0 (0xf76e3000)
    libc.so.6 => /lib32/libc.so.6 (0xf7588000)
    libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7535000)
    libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7418000)
    libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7408000)
    libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7404000)
    libuuid.so.1 => /lib32/libuuid.so.1 (0xf73fe000)
    /lib/ld-linux.so.2 (0xf777d000)
    libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf73e4000)
    libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf73de000)

```

---

### Post by tars_ac on 2011-04-22
Has anyone figured out how to get back to your Ubuntu desktop and leave the Citrix receiver running?  It is capturing alt-tabs etc, so I have to quit.  I can get to the terminal (CTRL-ALT-F1 etc), but that's not really what I want.  Any ideas?

---

### Post by mattflaschen on 2011-06-07
The instructions [posted above]("http://ubuntuforums.org/showpost.php?p=7005817&postcount=5"), originally by Mark Syms, worked for me on 10.10 x86-64 (Maverick).

---

### Post by dernsber on 2011-09-19
> **tars_ac said:**
> Has anyone figured out how to get back to your Ubuntu desktop and leave the Citrix receiver running?  It is capturing alt-tabs etc, so I have to quit.  I can get to the terminal (CTRL-ALT-F1 etc), but that's not really what I want.  Any ideas?

CTL+F2 than CTL+F9


Basically... CTL+F2 allows you to pass the next command through to the OS.  CTL+F9 minimizes your VDI.  you can CTL+F2 then Alt-Tab or change to a different desktop if you have those shortcuts setup... but minimizing is generally the most simple way to do that.

---

### Post by BigCityCat on 2011-10-15
This still works in Ubuntu 11.10. Using it with Gnome Shell. All though the download link is a little different now. Just click on the downloads tab and goto the citrix receiver.

---

### Post by kyle_p84 on 2011-10-16
Receiver version 12 is out for linux now

---

### Post by brion@cbkidder.com on 2011-10-16
Note that Citrix has a new Citrix Receiver 11, and it installs to a different directory. So you need to use the following to check dependencies:

ldd /opt/Citrix/ICAClient/wfcmgr

---

### Post by jms-ubuntu-en on 2011-10-20
> **kyle_p84 said:**
> Receiver version 12 is out for linux now

This works fine in 64bit Oneiric. However while there is a deb package for 64bit system, the receiver binary is still 32bit and therefore a manual mangling to set up a 32bit libXm.so.4 is needeed.

---

### Post by knife on 2011-10-26
I installed the 64 bit Citrix receiver v. 12 deb file in amd64 Oneiric with the amd64 libmotif4 package installed. It appears to have installed a plugin for firefox and/or some kind of shell integration, because I no longer had to tell firefox what app to use to open ica files as I did with prior versions. 

I can run the wfica client to open a connection to a remote server, but I can't seem to run wfcmgr.  The .desktop file doesn't respond and when I try it from a terminal, it tells me that libXm.so.4 is the wrong ELF class. Did citrix install a 64 bit client but a 32 bit wfcmgr?

---

### Post by guss606 on 2011-11-15
Hi guys, 

Hope you can help me with this, so here's what i did:

1. Download the client: [http://www.citrix.com/English/ss/dow...186&c1=sot2755](http://www.citrix.com/English/ss/dow...186&c1=sot2755)

2. Unpack the tar.gz: tar xfvz linuxx86-11.0.140395.tar.gz

3. Execute the install script: sudo ./setupwfc

4. Accept the default options (or whatever seems most appropriate)

5. Install openmotif: sudo apt-get install libmotif4

6. Run ldd to check for dependecy issues:ldd /home/ghassan/ICAClient/linuxx86/wfcmgr
	linux-gate.so.1 =>  (0x0093d000)
	libXm.so.4 => /usr/lib/libXm.so.4 (0x00301000)
	libXp.so.6 => /usr/lib/libXp.so.6 (0x0018d000)
	libXpm.so.4 => /usr/lib/libXpm.so.4 (0x00bce000)
	libSM.so.6 => /usr/lib/i386-linux-gnu/libSM.so.6 (0x00ad6000)
	libICE.so.6 => /usr/lib/i386-linux-gnu/libICE.so.6 (0x00110000)
	libXmu.so.6 => /usr/lib/libXmu.so.6 (0x00906000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0x001fd000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0x009de000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x0054f000)
	libXt.so.6 => /usr/lib/i386-linux-gnu/libXt.so.6 (0x0012a000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0x006cb000)
	libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0x00196000)
	libXft.so.2 => /usr/lib/i386-linux-gnu/libXft.so.2 (0x001a9000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0x00186000)
	libuuid.so.1 => /lib/i386-linux-gnu/libuuid.so.1 (0x001bf000)
	/lib/ld-linux.so.2 (0x00d7b000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0x001c5000)
	libfontconfig.so.1 => /usr/lib/i386-linux-gnu/libfontconfig.so.1 (0x00202000)
	libfreetype.so.6 => /usr/lib/i386-linux-gnu/libfreetype.so.6 (0x00e67000)
	libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0x00e2c000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0x001e4000)
	libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0x00b32000)
	libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0x00237000)

Now, when i log in to the Citrix site and click on "Desktop" or "RDP" or whatever, it downloads the launch.ica file and does nothing after that, if i click it, it opens with the text editor. 

Please help me here.

Oh, I'm using Ubuntu 11.10 x32bit :)

---

### Post by Zorrothustra on 2011-12-04
> **Zbor said:**
> After running ```
$ sudo cp -r /usr/lib/* /usr/lib32/
``` I get 
```
$ ldd /usr/lib/ICAClient/wfcmgr
    linux-gate.so.1 =>  (0xf771b000)
    libXm.so.4 => not found
    libXp.so.6 => not found
    libXpm.so.4 => not found
    libSM.so.6 => not found
    libICE.so.6 => not found
    libXmu.so.6 => not found
    libXinerama.so.1 => not found
    libdl.so.2 => /lib32/libdl.so.2 (0xf76f2000)
    libpthread.so.0 => /lib32/libpthread.so.0 (0xf76d9000)
    libc.so.6 => /lib32/libc.so.6 (0xf757e000)
    /lib/ld-linux.so.2 (0xf771c000)
    libXt.so.6 => not found
    libX11.so.6 => not found
```
What did I miss?

Everything looked fine before that

Seems like I've got the same problem as Zbor here. I'm not an expert at the command line, but I'm pretty sure I sort of messed up my lib and lib32 libraries through running ```
$ sudo cp -r usr/lib/* /usr/lib32/
``` 

The result from running ldd:

```
$ linux-gate.so.1 =>  (0xf7705000)
	libXm.so.4 => /usr/lib/libXm.so.4 (0xf748f000)
	libXp.so.6 => not found
	libXpm.so.4 => not found
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7485000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf746b000)
	libXmu.so.6 => not found
	libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf7467000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7461000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7446000)
	libc.so.6 => /lib32/libc.so.6 (0xf72cc000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7270000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf713a000)
	libXmu.so.6 => not found
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7126000)
	libXp.so.6 => not found
	libXft.so.2 => /usr/lib32/libXft.so.2 (0xf7110000)
	libuuid.so.1 => /lib32/libuuid.so.1 (0xf710a000)
	/lib/ld-linux.so.2 (0xf7706000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf70eb000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf70b5000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf701e000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf7013000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf700f000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7008000)
	libexpat.so.1 => /lib32/libexpat.so.1 (0xf6fdd000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf6fc8000)
```

My guess is I should somehow repair the lib and lib32 before anything else and then retry through the (right) instructions in this thread to get Citrix finally running... Just hope I didn't messed it up completely :-k 

Advise please.

---

