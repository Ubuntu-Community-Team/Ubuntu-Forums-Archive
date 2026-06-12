---
title: "HOWTO: Run Pro/Engineer WF 3.0 on Ubuntu 8.10"
date: 2008-11-22
forum: Tutorials
---

### Post by hambone79 on 2008-11-22
I'm writing this tutorial so that people can benefit from my experiences with setting up WF 3.0 on a HP xw4600 running Ubuntu 8.10. I work as a mechanical design engineer and CAD administrator, and I have been working on getting WF 3.0 running smoothly on Ubuntu for a few days now. After alot of Googling for answers and figuring out things on my own, I have finally come up with a solution that should work for everyone.

[SIZE="4"]**Getting Started**[/SIZE]

Before you can install Pro/E from CD or from the packages downloaded from PTC, you need to prep a few things on your system. First of all, you need to make sure that your graphics card is setup properly and that OpenGL is working. This is beyond the scope of this tutorial, so please check out the following links for more info:

[[COLOR="Purple"]Using Nvidia Binary Drivers[/COLOR]]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")
[[COLOR="Purple"]Using ATI Binary Drivers[/COLOR]]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

After you have OpenGL up and running, you need to install a few package so that you can run the Pro/E setup program. On my system I needed to install csh, libmotif3, libstdc++5, and portmap:

```

sudo apt-get install csh libmotif3 libstdc++5 portmap

```

Now you should be able to run the installer without any problems.

[SIZE="4"]**Running the Setup**[/SIZE]

You have two options for installing Pro/E: CD or online installer. it doesn't matter which one you use, just find the setup script and run it:

```

cd /path/to/proe
./setup

```

After this, the Pro/E setup program should launch and will run you through the installation steps. Just remember that you will need the license server information for your company, so have it handy when the program asks for it. If you are unsure of your license server or the license server triad, you can look at the launch scripts on another workstation to determine this information. Just open one of the following files in a text editor and search for "@7788".

**_On Windows:_**
C:\path\to\ProE\bin\proe.psf
[B][U]
On Unix/Linux:[/U][/B]
/path/to/ProE/bin/proe1

Keep in mind that alot of companies use custom Pro/E lanuch scripts that may be under a different name such as proewf3_b300 (for release 3.0 build 300). In this case you would need to look for the following files:
[B][U]
On Windows:[/U][/B]
C:\path\to\ProE\bin\proewf3_b300.psf
[B][U]
On Unix/Linux:[/U][/B]
/path/to/ProE/bin/proewf3_b300


[SIZE="4"]**Library Fix**[/SIZE]
Now you should have Pro/E installed, but if you attempt to run it you will get a bunch of "Locking assertion failed" error messages on the command line. This is the one thing that was keeping me from getting WF 3.0 working until I found this bug report:

[[COLOR="Purple"]https://bugs.launchpad.net/ubuntu/+source/libxcb/+bug/185311[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/libxcb/+bug/185311")

If you dig down through that bug, there is a post describing how to install a special version of libx11 that will prevent the Locking assertion errors and will allow Pro/E to run without any issues. The best part is that they wrote a script to automate the whole process and install the libraries outside of the package manager so that it does not affect Compiz or other applications.

You can download the script here:
[[COLOR="Purple"]http://launchpadlibrarian.net/16474477/install_libx11-noxcb_in_opt.sh[/COLOR]]("http://launchpadlibrarian.net/16474477/install_libx11-noxcb_in_opt.sh")

After you download the script, simply run it as follows (there is no need to run with sudo because it will do this for you):
```

sh install_libx11-noxcb_in_opt.sh

```

Once the script has completed, you will have a new copy of libx11 installed in /opt/LIBx11-noxcb that can be used to launch Pro/E, Matlab, Mathematica, and several other applications that give the "Locking assertion failed" error message.

Now on to the custom launch script

[SIZE="4"]**Custom Launch Script**[/SIZE]

Below is the custom launch script that I wrote to launch Pro/E on my workstation. The script will test to see if your working directory exits...if it doesn't it will create it for you. After this it will run a subroutine that will change to your working directory, set the LANG environment variable to "C", and disable compiz before launching Pro/E with the special libx11 libraries. When Pro/E is closed, the script will relaunch Compiz automatically.

```

#!/bin/bash
WORKING_DIR=$HOME/working
PROE_PATH=/usr/local/ptc/proeWildfire3.0/bin
PROE_PID='/sbin/pidof proe1' # This will depend on your custom Pro/E launchers

function launch_proe {
        cd $WORKING_DIR
        export LANG=C
        #Uncomment the line below if you are using Compiz
        metacity --replace &
        LD_LIBRARY_PATH=/opt/LIBx11-noxcb/lib:$LD_LIBRARY_PATH $PROE_PATH/proe &
        while [ -n "$PROE_PID" ]; do
                sleep 3
        done

        if [ -z "$PROE_PID" ]; then
                #Uncomment the line below if you are using Compiz
                compiz --replace &
        fi
}

if [ -d $WORKING_DIR ]; then
        launch_proe
else
        mkdir $WORKING_DIR
        launch_proe
fi


```

To use my script, simply copy the text into a file and call it whatever you want (I called my proe_starter), then make the script executable and launch it:

```

chmod +x proe_starter
./proe_starter

``` 

Once you are sure that the proe_starter script is function properly, you can copy it to local bin directory so that it will be in your path:

```

sudo chown root:root proe_starter
sudo cp proe_starter /usr/local/bin/

```

[SIZE="4"]**Create a Desktop Icon**[/SIZE]

You can create a desktop icon by right clicking on the desktop and selecting "Create Launcher". Just enter "proe_starter" in the Command field and give it a name and description. If you want to use the default Pro/E icons, they are located in "/path/to/proe/install/nt".

That pretty much wraps up this tutorial. If you have questions feel free to ask them.

---

### Post by keplerspeed on 2008-12-17
Thanks!! Especially for the script, well done!

I also want to add that visual effects ie compiz must be disabled for pro engineer and THE setup to work. I was pulling my hair out wondering why I couldnt run setup!!

---

### Post by ematlis on 2008-12-19
Thanks very much for this guide.  I use Fedora (7,8,9,10) and I also would see the locking assertion failed error.  I have another issue with PROE/Wildfire3 that I was hoping you might have some insight on.  The problem is with the "Mechanism" module in Proe.  It will not run on Fedora, although it does run on RHEL4, so there is probably some other library issue.  The exact error is: 'startup of application "MECHANIMS" failed'.  I can replicate this by opening a new assembly, then selecting Mechanism from the applications.  I'm not running compiz.

Oh, and after I quit from Proe, the proe_starter script doesn't exit.  Is there a way to make it do so?  

thanks!

---

### Post by hambone79 on 2008-12-22
I'm not sure about your Mechanisms issue, but it almost sounds like it is either 1) Not installed properly or 2) Not able to pull a license. You may want to check your startup script (i.e. /path/to/ProE/bin/proe1) and make sure you have the correct license feature selected (look for PROE_FEATURE_NAME=YOUR_PROE_FEATURE).

I will have to take a look at the script again. I noticed it was hanging up on my system the other day. I think it may have something to do with the subroutine that watches for the Pro/E process ID to disappear.

---

### Post by firefox66 on 2009-01-02
hi 
I have problem to execute proe1.So i just complete run pro/eng when i connect to the internet and then if i don't connect internet,i can not run pro/eng v3.

i'v checked file ptchostid in ptc/bin/ and each time i start it , i get new hostid.
And it's just stop renew my hostid when i connect to internet.

So what problem and how to solve ???

---

### Post by wolfenden on 2009-01-03
This thread has made a huge difference and I now have Pro E installed on 8.04.
However when I try and run Pro E it produces a message saying...
"Your chosen language en_US.UTF-8 is based on unicode, which this version of Pro/Engineer does not use. Pro/Engineer will shut down; please restart with a language that does not contain the string ".utf" or ".UTF"
I've tried British and Australian english, which does change the error message, but to know avail.  Can anyone advise me how to solve this?
Best
Robin

---

### Post by firefox66 on 2009-01-04
you can try this.it's complety succeed.i've tried it step-by-step.

[http://humdi.net/tips/how-to-disable-utf-8-in-console](http://humdi.net/tips/how-to-disable-utf-8-in-console)

---

### Post by opqr175 on 2009-01-04
Visit your favorite toy or game store and choose a mystery kit, invite as many guests as there are characters in the game, the invitations included in the kit contain complete profiles of victim, murderer, detectives and witnesses. [warcraft gold](http://goleveling.com/)

---

### Post by wolfenden on 2009-01-04
That looks great, newbie question though... How do you "open as root"? so as to be able to edit the necessary files.
I guess this'll be why the computer said I didn't have permission to stick ProE in it's default folder?
Best
R

---

### Post by l_square on 2009-01-22
since linux support is droped by PTC (don't know why) what options do we have?

---

### Post by dlovely on 2009-01-22
Im also a mechanical design engineer and CAD operator. My question: will this also work installing Autodesk Inventor and AutoCAD? Im not sure what to do. I've only been using Linux for two years now, still contemplating the idea of changing to Ubuntu. Currently using PClinuxOS dual boot with Windows XP

---

### Post by borissou on 2009-01-30
Hello,

I also have a problem to run the mechanism module. No solution so far. But during the installation, the file proe1 wasn't created. I'm using the one I have from version w2 but if someone can share its proe1 file, I will be grateful. Thanks.

Boris

---

### Post by fhansson on 2009-02-26
Thanks for the tips. I installed Pro Engineer under Ubuntu 8.10 and it will start up but I have problem with the mouse. It is "delayed" when pointing and selecting objects. I have seen others having the same problem under Ubuntu but I have no solution. Does anyone here has the same problem?

---

### Post by AlexVader on 2009-03-24
Hi Firefox,

I am having the same problem that you had with ProE 3 WF...

I Used to have a different lappy, Asus F3Jr, with Ubuntu 7.10 installed...

I used to set the ethernet card to connect at boot time, in the network manager, and leave my wireless in roaming mode...

This way, everytime i ran ptchostid, it would return the mac adress of my ethernet... which was the license mac adress...

Somehow in Ubuntu 8.10 AMD64 which I use now in my HP Dv5 1170 I cannot do this "trick"...

How do I set my ethernet to "plug" at boot time...?

I am facing exactly the same problem that you had...

Did you solve it...? How did you manage to do it...?

Best regards

Alex

---

### Post by dodjob on 2009-03-27
Hi all,
Its works for me :-) the only thing is that compiz doesn't start when I close Proe :-(
I'm a noob but hey.. a noob with Proe )
If someone knows how it's working with this < -z "$PROE_PID"  >
just to have it perfect actually ;-)
And.. Thank you!!!
H.

---

### Post by uwabaki on 2009-10-04
thanks for the tips
i had the same problem with compiz, fixed it with script used fo Eagle v.4, which had similar problems with compiz (curent version 5.6 is OK)

#!/bin/sh
WORKING_DIR=$HOME/proe/working # where ever you want
PROE_PATH=/home/"user"/proe/Wildfire3.0/bin # your install path

cd $WORKING_DIR
export LANG=en_US 
export XLIB_SKIP_ARGB_VISUALS=1
exec $PROE_PATH/proe

EDIT: found some problem, this script  works only if Compiz-Switch is used, if you switch off and on compiz using Compiz-Switch then it works, you could turn ProE on/off several times after using Compiz-Switch with no problems, dont know why

---

### Post by senttrox on 2009-12-25
Hi!

I have some problems... I have almost completed the instalation, but at the start I receive this message:

"WARNING: senttrox-desktop appears to have the loopback address 127.0.1.1 as IP address This may imply that processes on senttrox-desktop may not be able to connect to non-local processes NVIDIA: could not open the device file /dev/nvidiactl (Permission denied)."

PTC starts and then..

"License request failed for feature PROE_DDiTy: -8:
Invalid (inconsistent) license key.
Displaying status for license file: /home/senttrox/Documents/ptc_licfile.dat
License Server: none"

What is wrong?

---

### Post by senttrox on 2010-01-03
anyone...?:(

---

### Post by OCEAN11 on 2010-01-17
Thanks hambone for the tutorial on this install, which is very difficult to accomplish.

I'm wondering if anyone has been able to install Pro-E Wildfire 3.0 using the 64 bit version of Ubuntu 9.10?  I'm using the Ubuntu Ultimate Edition 64 bit version, but wondering if i can install a 32 bit version of Wildfire in a 64 bit version of Ubuntu ? My version of Wildfire is the student version. Thanks.

---

### Post by hambone79 on 2010-02-22
> **senttrox said:**
> Hi!

I have some problems... I have almost completed the instalation, but at the start I receive this message:

"WARNING: senttrox-desktop appears to have the loopback address 127.0.1.1 as IP address This may imply that processes on senttrox-desktop may not be able to connect to non-local processes NVIDIA: could not open the device file /dev/nvidiactl (Permission denied)."

PTC starts and then..

"License request failed for feature PROE_DDiTy: -8:
Invalid (inconsistent) license key.
Displaying status for license file: /home/senttrox/Documents/ptc_licfile.dat
License Server: none"

What is wrong?

For starters, you are using a pirated copy of Pro/Engineer.

---

### Post by hambone79 on 2010-02-22
> **OCEAN11 said:**
> Thanks hambone for the tutorial on this install, which is very difficult to accomplish.

I'm wondering if anyone has been able to install Pro-E Wildfire 3.0 using the 64 bit version of Ubuntu 9.10?  I'm using the Ubuntu Ultimate Edition 64 bit version, but wondering if i can install a 32 bit version of Wildfire in a 64 bit version of Ubuntu ? My version of Wildfire is the student version. Thanks.

I have done it before in a virtual machine to see if it was possible, but I can't find my notes on the installation process. If I remember correctly, I had to install the 32bit version of the Motiff libraries to make it work.

---

### Post by JorgeM93 on 2010-03-09
At least you can run it; I downloaded the torrent and managed myself to install it according to SHooTERS's instructions (installed also lobmotif3, tcsh, libstdc++5,etc). But it is frustrating that even though the launcher "proe1" belongs to my user and is marked as executable I get the error "Permission denied" (translated from Spanish) when executing ./proe1

Definitely, piracy doesn't worth it...  I hope I can use VariCAD as mt main CAD system soon.

---

### Post by octane70 on 2010-04-11
> **hambone79 said:**
> I have done it before in a virtual machine to see if it was possible, but I can't find my notes on the installation process. If I remember correctly, I had to install the 32bit version of the Motiff libraries to make it work.

Have any luck finding any notes on the installation process?
I have successfully installed Proe on 32 bit but now have switched to 64 bit and 
would appreciate any information that you may have to share.

thanks

---

### Post by afyounie on 2010-05-10
hambone,

I am trying to use the script that you wrote and am able to get the script to start proe and deactivate compiz, but when I shutdown proe, compiz doesn't come back. I read to uncomment certain things to make compiz work and I believe I did, but I don't know for sure. Below is the script as I have modified it for myself.

#!/bin/bash
WORKING_DIR=$HOME/Documents/pro_e_stuff
PROE_PATH=$HOME/ptc/bin
PROE_PID='/sbin/pidof proe1' # This will depend on your custom Pro/E launchers

function launch_proe {
        cd $WORKING_DIR
        export LANG=C
        #Uncomment the line below if you are using Compiz
        metacity --replace &
        LD_LIBRARY_PATH=/opt/LIBx11-noxcb/lib:$LD_LIBRARY_PATH $PROE_PATH/proe &
        while [ -n $PROE_PID ]; do
                sleep 3
        done

        if [ -z $PROE_PID ]; then
                #Uncomment the line below if you are using Compiz
                compiz --replace &
        fi
}

if [ -d $WORKING_DIR ]; then
        launch_proe
else
        mkdir $WORKING_DIR
        launch_proe
fi

This script is definitely very nice, just wish I could get it to work.

---

### Post by mutrax on 2013-02-09
Hey, I just went to the trouble of getting wf 3 running on precise 32 bit, and I thought yopu guys might find it useful.
NB.: It's a quick & dirty way, startup script could be nicer.

To run pro/e wf3 in precise 32 bit
========================
prior requirments;
make sure your gfx card is properly configured
Have a running licence server or locked licence
------------------------
Install required packages;
sudo apt-get install csh libmotif4 libstdc++5 portmap libxmu6 rpcbind
---------------------
Create libmotif3 symlinksin /usr/lib/

libMrm.so.3 -> libMrm.so.4
libUil.so.3 -> libUil.so.4
libXm.so.3 -> libXm.so.4

Ex;
sudo ln -s /usr/lib/lib????.so.4 /usr/lib/lib???.so.3
------------------------------
Get gtk 1.2 at [http://packages.ubuntu.com](http://packages.ubuntu.com), 
Download latest libgtk1.2-common, libglib1.2ldbl and libgtk1.2 
---------------------
Install proe WF3 (duh)
---------------------
Create startupscript for proe;
#!/bin/bash
gksudo service portmap stop
gksudo rpcbind -wi
export LANG=en_US
/usr/local/ptc/proeWildfire3.0/bin/proe

UPDATE, installing the gnome environement (described here [https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)), and disabling compiz (by running 'metacity --display=:0 --replace')  makes the in program tabs less twitchy.

Cheers,
):P

---

