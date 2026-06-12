---
title: "No tun module in 10.04 breaks my vpn client"
date: 2010-04-21
forum: Security
---

### Post by grahams on 2010-04-21
I use a SSLvpn-plus client

It's start up script looks for lsmod |grep tun. 

On 10.04 tun is in the kernel and not a module, so SSLvpn-plus fails to start. Is there a way to fake that is there?

---

### Post by cdenley on 2010-04-21
Why not edit the startup script?

---

### Post by grahams on 2010-04-21
Tried that, but then the daemon starts and then fails.

---

### Post by cdenley on 2010-04-21
> **grahams said:**
> Tried that, but then the daemon starts and then fails.

Then it sounds like "faking" lsmod output for the startup script isn't going to help with your problem.

---

### Post by jmercado on 2010-04-22
I am experiencing this same issue but with Juniper's Network Connect Client (error "Modprobe for Tun driver failed"). Does anyone have any other suggestions on how we can get around this?

---

### Post by cdenley on 2010-04-22
Sorry, I mixed up this thread with another VPN-related one.

---

### Post by grahams on 2010-04-23
VPN can't establish that is the issue.

BTW. anyone know why tun is in the kernel now rather than staying as a module? Unless most users use vpn this makes no sense IMHO.

---

### Post by cdenley on 2010-04-23
You can try this, at your own risk.
```

mkdir faketun
cd faketun
echo -e "#include <linux/module.h>\nstatic int start__module(void) {return 0;}\nstatic void end__module(void){return 0;}\nmodule_init(start__module);\nmodule_exit(end__module);">tun.c
echo -e "obj-m += tun.o\nall:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) modules\nclean:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) clean\nclean-files := Module.symvers">Makefile
make -C /lib/modules/`uname -r`/build/ M=`pwd`
sudo insmod tun.ko

```
I'm running 9.10 and already have a tun module, so I haven't tested it. It basically creates a kernel module "tun" which does nothing.

---

### Post by jmercado on 2010-04-23
I tried out your code but it doesn't seem to help my situation with Juniper's VPN client. It might help grahams because "lsmod |grep tun" returns a line for tun (not after reboot, but that's a good thing for me).

The Juniper Network Connect client checks for tun via modprobe tun and I still got "FATAL: Module tun not found."

Thanks for the code cdenley!

---

### Post by afriendinit on 2010-04-24
Any luck? I am facing the same issue. I saw a bug on this but it says invalid bug as the module is already a part of kernel. They should at least mention a work around. This is the reason why many folks don't  switch over...

---

### Post by cdenley on 2010-04-25
> **afriendinit said:**
> Any luck? I am facing the same issue. I saw a bug on this but it says invalid bug as the module is already a part of kernel. They should at least mention a work around. This is the reason why many folks don't  switch over...

Why would you expect them to mention a workaround for software they don't maintain, support, or use? If you stick to software in the ubuntu repository, you avoid these compatibility issues. Ubuntu developers have no control over your third party software.

---

### Post by rozbarwinek on 2010-04-25
So what to do?
Change permission to tuncfg? :D

---

### Post by cdenley on 2010-04-25
> **rozbarwinek said:**
> So what to do?
Change permission to tuncfg? :D

My suggestion is to use a VPN solution that is supported by, or at least compatible with, the OS you wish to use. Do you have the latest version? Is there any product support or forum on their website? Can you contact the author?

---

### Post by rozbarwinek on 2010-04-25
> **cdenley said:**
> My suggestion is to use a VPN solution that is supported by, or at least compatible with, the OS you wish to use. Do you have the latest version? Is there any product support or forum on their website? Can you contact the author?

I use hamachi :) it works very well except that I have to start TUN manually every reboot :P

---

### Post by afriendinit on 2010-04-25
not supported for.... you are developing an operating system not a toy for a kid. Hope you remember a concept called "backward compatibility".

---

### Post by OpSecShellshock on 2010-04-25
Seems to me that it's the developer of the client application who is most likely to be of assistance. They'll need to update the software such that it works with the new kernel, and in the meantime users with the current client will need to remain on a compatible version of the OS. Anyone tried checking the client developer's site for updates?

---

### Post by cdenley on 2010-04-25
> **afriendinit said:**
> not supported for.... you are developing an operating system not a toy for a kid. Hope you remember a concept called "backward compatibility".

There is a developer in this thread? A linux kernel developer? I'm not a developer, but it sounds like some VPN clients were written poorly with faulty assumptions.

---

### Post by afriendinit on 2010-04-26
I don't buy that. take a simple scenario:
if(x > 0) z=y/x;
now go to this particular scenario:
if(modprobe tun) open tunnel connection
else 
print error;

If scenario I is valid then definetly scenario II is also valid. May modprobe itself should intelligent enough such that it will not generate error if the module is built in...

I am a developer myself, this is just bad design from the OS side, they should expect every test case before going for something that might save a micro second or less during booting. This is poor response even after there is a bug.... 

If customer is always right then a user is also always right... in this case the vpn dev is the user and the OS dev is the merchant.

---

### Post by cdenley on 2010-04-26
> **afriendinit said:**
> 
I am a developer myself, this is just bad design from the OS side, they should expect every test case before going for something that might save a micro second or less during booting. This is poor response even after there is a bug.... 


If you're a developer, then I guess I will assume you understand this issue and the linux kernel better than I do, and have to take your word for it. I doubt the kernel team is going to read this thread, though. I disagree that modprobe should come tweaked to trick applications into thinking tun is loaded as a module when it is builtin to fix VPN clients which assumed it would always be loaded as a module.

---

### Post by HolyMurderer on 2010-04-28
Anyone found any solution for this "tun module failed" on Ubuntu 10.04 with Juniper? I can't use another VPN client, I'm on a big company, now I'm using Windows because of this problem...

---

### Post by cdenley on 2010-04-28
> **HolyMurderer said:**
> Anyone found any solution for this "tun module failed" on Ubuntu 10.04 with Juniper? I can't use another VPN client, I'm on a big company, now I'm using Windows because of this problem...

Isn't your big company paying for support? Ask Juniper Networks for a solution. I already posted my idea, but it is a little hard to fix a problem with software which I cannot obtain.

---

### Post by HolyMurderer on 2010-04-28
Yeah, try and tell a big company to pay for support for one or two guys who want to use linux, to use their vpn.
What will they say? The same you are doing, something I truly hate, which is discarding the case. And by the way, it's easier to ask for help on the specific Linux distribution forum, specially when it's that Linux distribution development team who decided to leave the standards and include a module on the kernel...

I'm trying with the community, if you don't want to help with other solutions, simpler, then don't say anything.

Is there any way of simulating the tun module, in order to make modprobe tun work, even if it doesn't make what it's supposed?

---

### Post by cdenley on 2010-04-28
> **HolyMurderer said:**
> Yeah, try and tell a big company to pay for support for one or two guys who want to use linux, to use their vpn.
What will they say? The same you are doing, something I truly hate, which is discarding the case. And by the way, it's easier to ask for help on the specific Linux distribution forum, specially when it's that Linux distribution development team who decided to leave the standards and include a module on the kernel...

I'm trying with the community, if you don't want to help with other solutions, simpler, then don't say anything.

Is there any way of simulating the tun module, in order to make modprobe tun work, even if it doesn't make what it's supposed?

I wasn't suggesting you ask your "big company" to go pay for support just for your problem. With enterprise software, usually businesses pay an annual fee for support. They may already be paying for support for the entire VPN solution, including the linux client.

I already posted how to create a fake kernel module. Now that I have 10.04 installed to a virtual machine, I'll see if I can get modprobe to see the module.

---

### Post by achim.wessling on 2010-04-28
I've the same issue with the Aventail VPN client my company uses. With 9.10 it worked like a charm!

Hope somebody finds a solution to this.

Achim

---

### Post by cdenley on 2010-04-28
```

sudo apt-get install build-essential linux-headers-`uname -r`
mkdir faketun
cd faketun
echo -e "#include <linux/module.h>\nstatic int start__module(void) {return 0;}\nstatic void end__module(void){return;}\nmodule_init(start__module);\nmodule_exit(end__module);">tun.c
echo -e "obj-m += tun.o\nall:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) modules\nclean:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) clean\nclean-files := Module.symvers">Makefile
make
sudo install tun.ko /lib/modules/`uname -r`/kernel/net/tun.ko
sudo depmod -a
sudo modprobe tun

```

---

### Post by achim.wessling on 2010-04-28
Yeap!

This works fine! Many Thanks!

Achim

---

### Post by cdenley on 2010-04-28
Glad it worked. If you upgrade your kernel, you will have to repeat that.

---

### Post by qweqwe1 on 2010-04-30
Thanks, that works indeed!

Just to help google find this post: snx works under ubuntu lucid. fix ssl extender. fake tun.

---

### Post by HolyMurderer on 2010-04-30
Thanks a lot, it worked ;)

Now I only would like Juniper to deliver a version compatible with 64-bit Sun Java, or even openJDK, so I can use 64-bit Linux full time.

---

### Post by ROBER1S on 2010-04-30
Many thanks, cdenley.  That fixed it for me as well (Kubuntu 10.04, 64-bit).

---

### Post by mikhmv on 2010-04-30
> **cdenley said:**
> ```

sudo apt-get install build-essential linux-headers-`uname -r`
mkdir faketun
cd faketun
echo -e "#include <linux/module.h>\nstatic int start__module(void) {return 0;}\nstatic void end__module(void){return;}\nmodule_init(start__module);\nmodule_exit(end__module);">tun.c
echo -e "obj-m += tun.o\nall:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) modules\nclean:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) clean\nclean-files := Module.symvers">Makefile
make
sudo install tun.ko /lib/modules/`uname -r`/kernel/net/tun.ko
sudo depmod -a
sudo modprobe tun

```
Hi, 

Could anybody like to write full path to "mkdir faketun"?
Thanks advance!

---

### Post by cdenley on 2010-04-30
> **mikhmv said:**
> Hi, 

Could anybody like to write full path to "mkdir faketun"?
Thanks advance!

What? That command makes a directory named "faketun" within your current working directory. The module will be compiled within that directory. What do you mean "full path"? Full path to what? The "mkdir" command?
```

which mkdir
/bin/mkdir faketun

```

---

### Post by mikhmv on 2010-04-30
Sorry. 

It is work....

---

### Post by cdenley on 2010-04-30
> **mikhmv said:**
> Sorry I asked wrong question....
before create directory "faketun"
I guess should be "cd SomeDirectory"
or mkdir /xxxx/xxxx/xxxx/faketun

Thanks

I still don't understand what you're asking. You can be in any directory you want when you start running those commands, as long as you have write permission, and there isn't already a directory named "faketun". Your home directory would work perfectly fine.

---

### Post by phelge on 2010-05-02
Many thanks cdenley, it fixed my Aventail client!

---

### Post by rozbarwinek on 2010-05-02
Why not just use "sudo /sbin/tuncfg"?

Just change permissions and make it executable by user, add it to autostart and your done.

Easier and you don't need to recompile kernel every time :D

---

### Post by cdenley on 2010-05-02
> **rozbarwinek said:**
> Why not just use "sudo /sbin/tuncfg"?

Just change permissions and make it executable by user, add it to autostart and your done.

Easier and you don't need to recompile kernel every time :D

That command is not provided by any ubuntu package. Is that part of one of the VPN clients discussed in this thread? Perhaps you should be more specific.

---

### Post by rozbarwinek on 2010-05-02
> **cdenley said:**
> That command is not provided by any ubuntu package. Is that part of one of the VPN clients discussed in this thread? Perhaps you should be more specific.

I'm sorry, a hamachi client :)
Will it make my system less secure?

---

### Post by cdenley on 2010-05-02
> **rozbarwinek said:**
> I'm sorry, a hamachi client :)
Will it make my system less secure?

I have no idea. The only VPN client I ever used in ubuntu was openvpn from the repos. I haven't used in lucid yet, but I doubt it requires my sloppy workaround. I don't know what any hamachi commands do.

---

### Post by john_navarro on 2010-05-02
It appears that TUN disappeared with the 2.6.32-21 kernel. When I use 2.6.32-20 my SNX client works just fine. 

I tried to use the TUN fake script, but it doesn't seem to work with my 64 bit install. I get the following error:

make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
install: cannot stat `tun.ko': No such file or directory
FATAL: Module tun not found.

---

### Post by kazersozet on 2010-05-03
> **cdenley said:**
> ```

sudo apt-get install build-essential linux-headers-`uname -r`
mkdir faketun
cd faketun
echo -e "#include <linux/module.h>\nstatic int start__module(void) {return 0;}\nstatic void end__module(void){return;}\nmodule_init(start__module);\nmodule_exit(end__module);">tun.c
echo -e "obj-m += tun.o\nall:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) modules\nclean:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) clean\nclean-files := Module.symvers">Makefile
make
sudo install tun.ko /lib/modules/`uname -r`/kernel/net/tun.ko
sudo depmod -a
sudo modprobe tun

```


Cdenley  thank you, the window "network connect" opens normally, but I have a  new error message that appears "session expired".
no problem with ubuntu 9.10 and Seven.

---

### Post by cdenley on 2010-05-03
> **kazersozet said:**
> Cdenley  thank you, the window "network connect" opens normally, but I have a  new error message that appears "session expired".
no problem with ubuntu 9.10 and Seven.

You haven't mentioned what VPN client you're using, but I probably don't know anything about it or any "session expired" errors it might give you.

---

### Post by Nokrosis on 2010-05-03
Hi cdenley, 
i have Ubuntu 10.4 64bit and i implemented your solution. I got no errors but 'modprobe tun' outputs anything and when i start Juniper Network Connect it output no errors but it only sent me back to the start button screen.  Do you have any idea why is this happening??

If there's no solution can you post the 'undo' script for faketun you supplied?

Thank's a lot for your help.

---

### Post by cdenley on 2010-05-03
> **Nokrosis said:**
> Hi cdenley, 
i have Ubuntu 10.4 64bit and i implemented your solution. I got no errors but 'modprobe tun' outputs anything and when i start Juniper Network Connect it output no errors but it only sent me back to the start button screen.  Do you have any idea why is this happening??

If there's no solution can you post the 'undo' script for faketun you supplied?

Thank's a lot for your help.

I assume you mean "sudo modprobe tun" doesn't output anything. If so, then the fake module was loaded, and is working as it should. What is a "start button screen"? I don't know anything about Juniper software. 

To remove the fake module:
```

sudo rmmod tun
sudo rm /lib/modules/`uname -r`/kernel/net/tun.ko
sudo depmod -a

```

---

### Post by Nokrosis on 2010-05-03
Thanks cdenley, i finally managed to connect to the VPN, i think your solution did just part of the work for me, since i was having a further error now with **libncui** running under 64bit system.

If it helps anyone, here's where i found the workaround for libncui problem on 64bit systems:

[http://makefile.com/.plan/2009/10/27/juniper-vpn-64-bit-linux-an-unsolved-mystery](http://makefile.com/.plan/2009/10/27/juniper-vpn-64-bit-linux-an-unsolved-mystery)

Thank's a lot.

---

### Post by kazersozet on 2010-05-03
> **cdenley said:**
> You haven't mentioned what VPN client you're using, but I probably don't know anything about it or any &quot;session expired&quot; errors it might give you.

hi,
I use  the Juniper VPN client to connect the SA2500 model. Before using the code, I had a problem with modprobe  tun and now I have time out after authentication and once the tunnel  ipsec up

---

### Post by cdenley on 2010-05-03
> **kazersozet said:**
> hi,
I use  the Juniper VPN client to connect the SA2500 model. Before using the code, I had a problem with modprobe  tun and now I have time out after authentication and once the tunnel  ipsec up

Well I don't know how to fix problems with Juniper's VPN client.

---

### Post by kazersozet on 2010-05-03
> **cdenley said:**
> Well I don't know how to fix problems with Juniper's VPN client.


Thank  you, I would say that the service working again with my ubuntu 10.04.

---

### Post by ds9 on 2010-05-04
There is a bug officially reported :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565856?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565856?comments=all)

Please clik on the link : This bug affects you
so that we get an updated kernel ASAP :)

---

### Post by linuxtechie on 2010-05-05
> **ds9 said:**
> There is a bug officially reported :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565856?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565856?comments=all)

Please clik on the link : This bug affects you
so that we get an updated kernel ASAP :)


It seems that this issue doesn't affect 32bit env. At the moment I am connected to my office VPN, however that error did popup, but the connection didn't fail.

Nevertheless, thanks cdenley!

+LT

---

### Post by aravinds on 2010-05-05
> **cdenley said:**
> You can try this, at your own risk.
```

mkdir faketun
cd faketun
echo -e "#include <linux/module.h>\nstatic int start__module(void) {return 0;}\nstatic void end__module(void){return 0;}\nmodule_init(start__module);\nmodule_exit(end__module);">tun.c
echo -e "obj-m += tun.o\nall:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) modules\nclean:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) clean\nclean-files := Module.symvers">Makefile
make -C /lib/modules/`uname -r`/build/ M=`pwd`
sudo insmod tun.ko

```I'm running 9.10 and already have a tun module, so I haven't tested it. It basically creates a kernel module "tun" which does nothing.

Hi,

Thank you for this.

I executed all the above commands that you gave and am no longer receiving the 'modprobe for tun driver failed' error.

However, the moment Juniper Network Connect 6.5 connects to my company's VPN, i am disconnected with 'Session Timeout'.

Can you pls suggest what could be the issue?

Ubuntu 10.04 LTS 32-bit.

>>It basically creates a kernel module "tun" which does nothing.
I *think* this might be the problem? i.e. the tun module might be there for a reason, and just compiling a dummy tun module, while satisfying the requirement that a tun module has to be present, might not be offering some feature(s) thats necessary for Juniper Network Connect to connect/establish session. Nevertheless, I am not an expert on this...

---

### Post by kitepilot on 2010-05-05
Hello World:

I created and installed the faked tun driver, that gave Juniper's shell  script satisfaction and happiness.  After that, I got the timeout  problem.

I uninstalled Open Source Java and installed Sun's.
Now everything works.
YMMV...

THANKS everyone!
Enrique A. Troconis

---

### Post by cdenley on 2010-05-05
> **aravinds said:**
> 
I *think* this might be the problem? i.e. the tun module might be there for a reason, and just compiling a dummy tun module, while satisfying the requirement that a tun module has to be present, might not be offering some feature(s) thats necessary for Juniper Network Connect to connect/establish session. Nevertheless, I am not an expert on this...

If you read the entire thread, you would know that the issue is that the tun driver is now builtin to the kernel, not installed as a kernel module. The necessary features are all there, the only problem is that Juniper assumes if it fails to load a module named "tun", they aren't. This is a faulty assumption.

---

### Post by aravinds on 2010-05-06
> **kitepilot said:**
> Hello World:

I created and installed the faked tun driver, that gave Juniper's shell  script satisfaction and happiness.  After that, I got the timeout  problem.

I uninstalled Open Source Java and installed Sun's.
Now everything works.
YMMV...

THANKS everyone!
Enrique A. Troconis

Perfect! That did it.

For the benefit of others, here are the complete step-by-step instructions:
0. Run the following. Press 'Y' wherever you are asked.
1. Go to Applications > Ubuntu Software Center > Installed Software.
2. Find Open Java in the list and click Remove. This may prompt you to remove browser plugin as well, click ok.
3. After the uninstall is done, close the Software center and open a terminal.
4. ```
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  lucid partner
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```   This assumes that you have 32 bit version of Ubuntu installed. NOTE: If you get a 'Accept JRE license terms' prompt within the terminal, you have to hit TAB to highlight the OK button and then hit ENTER to accept. (I spent 20 mins trying to figure out how I could 'click' on the OK button within the terminal :) )
5. Then run the commands given by cdenley:

> **cdenley said:**
> ```

sudo apt-get install build-essential linux-headers-`uname -r`
mkdir faketun
cd faketun
echo -e "#include <linux/module.h>\nstatic int start__module(void)  {return 0;}\nstatic void  end__module(void){return;}\nmodule_init(start__module);\nmodule_exit(end__module);">tun.c
echo -e "obj-m += tun.o\nall:\n\tmake -C /lib/modules/\$(shell uname  -r)/build/ M=\$(PWD) modules\nclean:\n\tmake -C /lib/modules/\$(shell  uname -r)/build/ M=\$(PWD) clean\nclean-files :=  Module.symvers">Makefile
make
sudo install tun.ko /lib/modules/`uname -r`/kernel/net/tun.ko
sudo depmod -a
sudo modprobe tun

```

6. After that, visit your company's website and install Juniper Network Connect.
7. It should now start properly without the 'modprobe for tun driver failed' error and it will not timeout once connected.

Thanks to cdenley and kitepilot!

---

### Post by kazersozet on 2010-05-06
> **aravinds said:**
> Perfect! That did it.

For the benefit of others, here are the complete step-by-step instructions:
1. Go to Applications > Ubuntu Software Center > Installed Software.
2. Find Open Java in the list and click Remove. This may prompt you to remove browser plugin as well, click ok.
3. After the uninstall is done, close the Software center and open a terminal.
4. Type, without quotes, "sudo aptitude install sun-java6-plugin sun-java6-jdk sun-java6-jre". This assumes that you have 32 bit version of Ubuntu installed. NOTE: If you get a 'Accept JRE license terms' prompt within the terminal, you have to hit TAB to highlight the OK button and then hit ENTER to accept. (I spent 20 mins trying to figure out how I could 'click' on the OK button within the terminal :) )
5. Then run the commands given by cdenley:



6. After that, visit your company's website and install Juniper Network Connect.
7. It should now start properly without the 'modprobe for tun driver failed' error and it will not timeout once connected.

Thanks to cdenley and kitepilot!


It works fine
Thinks [aravinds]("http://ubuntuforums.org/member.php?u=1067682") cdenley  and kitepilot

---

### Post by cdenley on 2010-05-06
> **aravinds said:**
> 
5. Then run the commands given by cdenley:

Wrong code. That builds the fake module, but doesn't install it where modprobe can find it.
> **cdenley said:**
> ```

sudo apt-get install build-essential linux-headers-`uname -r`
mkdir faketun
cd faketun
echo -e "#include <linux/module.h>\nstatic int start__module(void) {return 0;}\nstatic void end__module(void){return;}\nmodule_init(start__module);\nmodule_exit(end__module);">tun.c
echo -e "obj-m += tun.o\nall:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) modules\nclean:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) clean\nclean-files := Module.symvers">Makefile
make
sudo install tun.ko /lib/modules/`uname -r`/kernel/net/tun.ko
sudo depmod -a
sudo modprobe tun

```

---

### Post by XProgrammer on 2010-05-07
Thanks all. Its working now. :).

---

### Post by karlvirgil on 2010-05-07
Thanks so much for posting this solution.  It worked for me to fix my issue with SSL Network Extender on Lucid Lynx.

---

### Post by Arrgh on 2010-05-07
This worked more or less, but I got stuck on the timeout problem with the vpn client I have.

Hours of bashing away at trying to install the Sun Java instead of this <snip> openjdk eventually led me to the following, which worked:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Just an fyi in case others are trying to get it to work and are stuck on openjdk

---

### Post by cwchien on 2010-05-07
Thanks a lot!

I got my CheckPoint SSL Network Extender works again.

Ubuntu 10.4 32-bit
Firefox 3.6.3
Sun Java 1.6.20

---

### Post by aravinds on 2010-05-10
> **cdenley said:**
> Wrong code. That builds the fake module, but  doesn't install it where modprobe can find it.
Fixed, thanks

---

### Post by Procrastes on 2010-05-10
Thanks!

---

### Post by RgnKjnVA on 2010-05-10
lucid lynx, 32-bit I get...

```

Couldn't find any package whose name or description matched "sun-java6-plugin"
No candidate version found for sun-java6-jdk
No candidate version found for sun-java6-jre
Couldn't find any package whose name or description matched "sun-java6-plugin"
No candidate version found for sun-java6-jdk
No candidate version found for sun-java6-jre
The following packages will be REMOVED:
  ca-certificates-java{u} icedtea-6-jre-cacao{u} java-common{u} linux-headers-2.6.32-21{u} 
  linux-headers-2.6.32-21-generic{u} openjdk-6-jre-headless{u} openjdk-6-jre-lib{u} 
  tzdata-java{u} 
0 packages upgraded, 0 newly installed, 8 to remove and 9 not upgraded.
Need to get 0B of archives. After unpacking 176MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.

```

Backed out the changes and replaced Openjdk but now Juniper now telling me "JRE not installed/Java is disabled." i.e. worse than when I started (modprobe error)

---

### Post by cdenley on 2010-05-10
sun-java6 is in the partner repo. You need to enable it.
```

sed -e 's/# *deb \(.*\) lucid partner/deb \1 lucid partner/g' /etc/apt/sources.list|sudo tee /etc/apt/sources.list
sudo apt-get update
sudo apt-get install sun-java6-plugin

```

---

### Post by RgnKjnVA on 2010-05-11
Have it sorted out and now connecting via Juniper. Thanks all

---

### Post by Nodaki on 2010-05-11
Thanks to cdenley for the help here.  I am now able to use Juniper's Network Connect over SSL.

It took the combination of cdenley's work creating the tun mod, the removal of Open Java, and the installation of Sun Java to get me up and running.

SSL
Juniper
Network Connect
10.04

Michael Barbere

---

### Post by psypher on 2010-05-12
> **cdenley said:**
> I have no idea. The only VPN client I ever used in ubuntu was openvpn from the repos. I haven't used in lucid yet, but I doubt it requires my sloppy workaround. I don't know what any hamachi commands do.

FYI openvpn requires the sloppy workaround, fixed it, thanks

---

### Post by PugTheBlack on 2010-05-14
Alternative solution is out there aswell, [Using Juniper Network Connect on Ubuntu]("http://mad-scientist.net/juniper.html"). 

This method has worked very well for me on both 32 and 64 bit installs of 10.04. 

-M-

---

### Post by psorcerer on 2010-05-18
I think I have better solution that will work even for future kernels without recompilation.

```

echo -e "install tun /bin/true\n" > built-in.conf
sudo cp built-in.conf /etc/modprobe.d/

```

---

### Post by onemorepash on 2010-05-20
Hi all,

You guys are finding a solution for a nonexisting issue. Juniper's SSL VPN Network Connect works well with tun built into the kernel. It just shows up a warning ‘modprobe for tun failed’ and that's all. Believe me, I've been using (well, and selling) it since 2006, time when I was young enough to compile linux kernels for myself.

Cdenley's code is, though useful (thanks, cdenley!), just a way to shut up the warning. Nothing else. You'll most probably see ‘session timeout’ warning the next and NC session will terminate.

The real issue is that Sun Java was moved from official Ubuntu distribution. Juniper NC doesn't want to work with OpenJDK. The solution is here (and it is quite simple).
Just add/uncomment the following in your /etc/apt/sources.list:

```
deb http://archive.canonical.com/ubuntu lucid partner
```and say
```
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```Than restart Firefox and try to run NC.

Doesn't matter if you used cdenley's code or not.

BTW, you guys have became too choosy (sorry). Sun Java had not been a part of loads of distros for ages and it had never been a problem to get it even under Slackware.

PutTheBlack's link ([http://mad-scientist.net/juniper.html](http://mad-scientist.net/juniper.html)) is also worth to check. Specially if you run _64 (not really a Juniper's fault. 64-bit Java does not support Applets even for Windows).

--
Regards,
Pavel

---

### Post by cdenley on 2010-05-20
> **onemorepash said:**
> 
Juniper's SSL VPN Network Connect works well with tun built into the kernel. It just shows up a warning &#8216;modprobe for tun failed&#8217; and that's all.

I think someone said that was the case on 32-bit, but not 64-bit. Or maybe it was the other way around. If psorcerer's solution works, though, that would be much better.

---

### Post by onemorepash on 2010-05-21
> **cdenley said:**
> I think someone said that was the case on 32-bit, but not 64-bit. Or maybe it was the other way around. If psorcerer's solution works, though, that would be much better.

I meant in case of Juniper NetworkConnect it does not really matter whether TUN driver is a module or a part of core kernel code.  So it's common for 32 and 64. If Tun is hard-compiled, NC just shows a warning which does not really mean anything. SSL VPN should work after it. Dummy tun module only helps to shut the warning up, it does not help to make NC working.

Why NC does not want to work on Ubuntu 10.04 is that Sun Java was replaced with OpenJDK. So the real solution is to install Sun Java.

64-bit is another story. It has never worked since 64-bit Java does not support Applets. The workaround is to use 32-bit browser with 32-bit Sun Java.

---

### Post by cdenley on 2010-05-21
> **onemorepash said:**
> So it's common for 32 and 64.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565856?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565856?comments=all)
> 
So at least the Juniper VPN client (I use v6.5) works with the generic kernel - **but 32bit java only, not with 64bit**.
The warning "modprobe for tun module failed" is still there but the client itself works as it should do.


---

### Post by onemorepash on 2010-05-22
HI cdenley,

I don't argue. Your second quote from Marchel Schulte's is exactly what I mean.

There are actually 3 issues in one:

1. Tun warning problem, which can be resolved with dummy module is related to kernel so there is no difference. This is what I meant writing ‘it is common for 32 and 64’.

2. Sun/Oracle Java is, I believe, also replaced with OpenJDK in both 32 and 64 versions on Ubuntu lucid. Though I did not tested 64 mysef.

3. Sun Java 64-bit does not support applets and web start: [http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com) (‘Please use the 32-bit version for Java applet and Java Web Start  support’). This is the real problem with 64-bit if one wants to use Juniper Network Connect. The solution is to use 32-bit bowser and 32-bit Java. When I had been using 64-bit for several months a year ago, I managed to use Firefox 64 for everything and SeaMonkey 32 just to run NetworkConnect. Worked well, but since I don't really have much reasons to run 64 this was why I moved back to 32-bit.

Well, I really believe it is more than clear now and don't see a need to continue :)

---

### Post by mguznt on 2010-05-22
I'm having the same problem with juniper vpn not working.  How did you manage to install a 32 bit browser on your 64 bit system?  I google and can't find a nice how to.  

Cheers!

---

### Post by onemorepash on 2010-05-23
> **mguznt said:**
> I'm having the same problem with juniper vpn not working.  How did you manage to install a 32 bit browser on your 64 bit system?  I google and can't find a nice how to.  

Check this link: [http://mad-scientist.net/juniper.html](http://mad-scientist.net/juniper.html) provided by someone above. Seems like there is a way to run Java-32 with 64 bit browsed. At least the author managed to run Juniper NC under Ubuntu 64 somehow.

I did not install 32 bit browser on Ubuntu 64, but I did so with Centos. Yum, IFAIR, allows to explicitly select architecture. It installs a lot of 32 but libraries if you want to run a single 32 bit program on 64 bit OS. Don't know how to do this with apt though did not even tried.

---

### Post by aravinds on 2010-06-04
After almost a month of using SSL VPN (Juniper) without any timeout issues or tun errors, I can say that its working well. I have summarized the good work of cdenley and others here ->

[http://art.ubuntuforums.org/showpost.php?p=9246896&postcount=54](http://art.ubuntuforums.org/showpost.php?p=9246896&postcount=54)

Platform:
Ubuntu Lucid
32 bit OS
Juniper SSL Network Connect

---

### Post by dunnerz on 2010-06-05
> **aravinds said:**
> After almost a month of using SSL VPN (Juniper) without any timeout issues or tun errors, I can say that its working well. I have summarized the good work of cdenley and others here ->

[http://art.ubuntuforums.org/showpost.php?p=9246896&postcount=54](http://art.ubuntuforums.org/showpost.php?p=9246896&postcount=54)

Platform:
Ubuntu Lucid
32 bit OS
Juniper SSL Network Connect

Thank you. Worked perfect for me:

Ubuntu 10.04
64bit OS
SNX network extender

(note, I had already installed the libstdc binaries and run preload on them, ie:
LD_PRELOAD=/usr/lib/libstdc++.so.5.0.7 snx ......

with those added tun steps, it worked.

thanks.

---

### Post by soljin on 2010-06-19
I have tried both the fake TUN:

[http://art.ubuntuforums.org/showpost.php?p=9246896&postcount=54](http://art.ubuntuforums.org/showpost.php?p=9246896&postcount=54)

and the mad scientist approach:

[http://mad-scientist.net/juniper.html](http://mad-scientist.net/juniper.html)

Both get me to the point where I connect but I am instantly disconnected.  I assume this is because of 64 bit TUN drivers but I am not sure.

I am on 64 bit Ubuntu 10.04, Dunnerz can you be more specific as to what else you did to get it working?

Thanks!

---

### Post by psypher on 2010-06-21
> **soljin said:**
> I have tried both the fake TUN:

[http://art.ubuntuforums.org/showpost.php?p=9246896&postcount=54](http://art.ubuntuforums.org/showpost.php?p=9246896&postcount=54)

and the mad scientist approach:

[http://mad-scientist.net/juniper.html](http://mad-scientist.net/juniper.html)

Both get me to the point where I connect but I am instantly disconnected.  I assume this is because of 64 bit TUN drivers but I am not sure.

I am on 64 bit Ubuntu 10.04, Dunnerz can you be more specific as to what else you did to get it working?

Thanks!
I am also using 64 bit and I had to follow this guy's instructions. It's an adaption of the mad scientitst script. It's a bit tedious but at least I can do my work:

[http://makefile.com/.plan/2009/10/27/juniper-vpn-64-bit-linux-an-unsolved-mystery](http://makefile.com/.plan/2009/10/27/juniper-vpn-64-bit-linux-an-unsolved-mystery)

---

### Post by dunnerz on 2010-06-21
> **soljin said:**
> I have tried both the fake TUN:

[http://art.ubuntuforums.org/showpost.php?p=9246896&postcount=54](http://art.ubuntuforums.org/showpost.php?p=9246896&postcount=54)

and the mad scientist approach:

[http://mad-scientist.net/juniper.html](http://mad-scientist.net/juniper.html)

Both get me to the point where I connect but I am instantly disconnected.  I assume this is because of 64 bit TUN drivers but I am not sure.

I am on 64 bit Ubuntu 10.04, Dunnerz can you be more specific as to what else you did to get it working?

Thanks!

These are the steps I followed (this is for snx, guessing other clients would be similar)

Install compat library from [http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)

( snx is quite an old program, and looks for 32bit libs, the above installs 64/default libs; luckily the libs work on both architectures, just about, so doing the following will make snx work )

```

cd /usr/lib32
cp ../lib/libstdc++.so.5* .
sudo LD_PRELOAD=/usr/lib/libstdc++.so.5.0.7 snx -s[SERVER], etc.

```

(where "snx" is your vpn client)

I hope that helps? If it does, you can make it a bit simpler but doing this:

```

sudo mv /usr/bin/snx /usr/bin/snx-bin
sudo gedit /usr/bin/snx

//add this line to the above file you opened
LD_PRELOAD=/usr/lib/libstdc++.so.5.0.7 /usr/bin/snx-bin "$@" '

sudo chmod u+rsx /usr/bin/snx
sudo chmod go+x /usr/bin/snx


```

For 10.04, I then followed the tun instructions

---

### Post by markdjones82 on 2010-07-10
I as well am getting disconnected automatically after trying the fixes as well.

It is the juniper client and I am running 10.04 32 bit.

It worked before the upgrade.

---

### Post by anu815 on 2010-07-16
I had similar issues with the Appgate VPN client.  I can't remember where I found this so I can't give due credit but the following sorted out the issues with the Appgate client for me: -

Add the following line to /etc/modprobe.d/modprobe.conf: -

install tun /bin/true

I hope this helps...!

---

### Post by zipizap on 2010-08-17
If you only want to use JUNIPER NETWORK CONNECT in ubuntu 10.04, then simply follow the (very simple and effective) instructions posted in [http://www.ubuntugeek.com/howto-setup-juniper-network-connect-vpn-on-ubuntu-9-10.html](http://www.ubuntugeek.com/howto-setup-juniper-network-connect-vpn-on-ubuntu-9-10.html)
which I leave resumed below:


> 
[I]**Problem** You may not connect to your company private [VPN[IMG]http://images.intellitxt.com/ast/adTypes/mag-glass_10x10.gif[/IMG]]("http://www.ubuntugeek.com/howto-setup-juniper-network-connect-vpn-on-ubuntu-9-10.html#")  via Juniper Network Connect. After You click on the [start] button of  the Network Connect prompt on the Juniper Network VPN screen, You got  the error message saying  “JRE is disabled or not installed”.

**Solution**[/I]  [I]
 1.  Install Sun Java runtime
 2. Create a root password and give it to the Juniper setup program  when it asks for it. You only need to do this on the first connect. Then  ignore such request thereafter.
 3. Restart the browser and start the Network Connect again. It should work.
 1.Install Sun Java runtime[/I]



In the original post, there are step-by-step instructions of how to do it.


After a fresh install of xubuntu 10.04, this made Juniper Network Connect tunnel work fine and in 2 minutes


cheers

---

### Post by COKEDUDE on 2010-08-25
> **aravinds said:**
> Perfect! That did it.

For the benefit of others, here are the complete step-by-step instructions:
0. Run the following. Press 'Y' wherever you are asked.
1. Go to Applications > Ubuntu Software Center > Installed Software.
2. Find Open Java in the list and click Remove. This may prompt you to remove browser plugin as well, click ok.
3. After the uninstall is done, close the Software center and open a terminal.
4. ```
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  lucid partner
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```   This assumes that you have 32 bit version of Ubuntu installed. NOTE: If you get a 'Accept JRE license terms' prompt within the terminal, you have to hit TAB to highlight the OK button and then hit ENTER to accept. (I spent 20 mins trying to figure out how I could 'click' on the OK button within the terminal :) )
5. Then run the commands given by cdenley:



6. After that, visit your company's website and install Juniper Network Connect.
7. It should now start properly without the 'modprobe for tun driver failed' error and it will not timeout once connected.

Thanks to cdenley and kitepilot!

Thx for the detailed steps.

---

### Post by arpoodle on 2010-12-07
There still doesn't seem to be a proper fix for this on 64 bit Ubuntu.

Using 10.4, 32 bit most of the fixes here, involving a fake tun module, worked fine. I've just upgraded my laptop and have installed 64bit Ubuntu, and now, none of the "fixes" help apart from extracting the cookie information from the web page and executing a command line app to open the connection.

Certainly a far from elegant solution.

Otherwise, the java app completes it's loading progress, dumps you back at the start page and does nothing.

---

### Post by Nodaki on 2011-03-29
Thread needs a bump due to recent updates.  Updates broke the functionality of Juniper SSL VPN on 10.04 Lucid.

Required a removal of OPEN Java again and a reinstall of Sun Java plugins.  I did not need to use cdenley's steps again.  A removal and reinstall of Java was all that was required.

Cheers,

MB

---

