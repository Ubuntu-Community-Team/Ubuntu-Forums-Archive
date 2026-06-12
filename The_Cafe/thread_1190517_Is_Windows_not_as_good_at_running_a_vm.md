---
title: "Is Windows not as good at running a vm?"
date: 2009-06-18
forum: The Cafe
---

### Post by swoll1980 on 2009-06-18
I've been using Linux for over 2 years, and I bounce back, and forth for various reasons. One thing that I notice is that When I'm using Windows the vms run like crap. Whether I use vmware, or VirtualBox, they just run really slow. I'm not crazy, and this is really happening, I would like to know if this is a problem most people have, and if so, do you have anything that would explain it?

---

### Post by Viva on 2009-06-18
Windows is crap at running almost everything:)

---

### Post by Dark Aspect on 2009-06-18
> **swoll1980 said:**
> Whether I use vmware, or VirtualBox, they just run really slow. I'm not crazy

vmware, in my experience, is always slow in comparison to Virtualbox.

> **swoll1980 said:**
> do you have an explanation that would explain it?

Windows is a horrible OS maybe?

---

### Post by swoll1980 on 2009-06-18
I said "Do you have any explanation that would explain it?" lol That sounds pretty stupid.

---

### Post by swoll1980 on 2009-06-18
> **Viva said:**
> Windows is crap at running almost everything:)

It seems to run Firefox pretty well.

---

### Post by thisllub on 2009-06-18
Windows is in many ways a safer bet inside a VM.
When it takes a dump you just restore from backup.

---

### Post by swoll1980 on 2009-06-18
> **thisllub said:**
> Windows is in many ways a safer bet inside a VM.
When it takes a dump you just restore from backup.

I'm talking about Windows as a host seems to be no good.

---

### Post by aeiah on 2009-06-18
im guessing HyperV or whatever its called would be good since it offers paravirtualisation / hardware virtualisation and all that fancy stuff, but that's only really useful if you're wanting to run windows virtual machines. only other solution that'll do that as far as i know is Xen with suse enterprise (because it involves a microsoft kernel mod that you have to pay for).

if i recall, i never had any problems with windows running vmware though.

what are you trying to achieve? just checking out distros or what?

---

### Post by Simian Man on 2009-06-18
This is a *total* guess but Virtualbox on Linux installs two kernel modules.  Perhaps being able to add to the kernel gives it a performance benefit.  I have no idea how Vbox runs on Windows...

---

### Post by swoll1980 on 2009-06-18
> **aeiah said:**
> 

what are you trying to achieve? just checking out distros or what?

I couldn't afford my vonage bill, so I'm using the magicjack as my main phone. In order to achieve this, I have to leave windows running all the time. Being the Ubuntu addict that I am, I installed it in a vm on the Windows host. It runs like crap though. The guests on my Windows host always run like crap. When I use Ubuntu as the host they run so smooth, you wouldn't even be able to tell it was a vm.

---

### Post by Pogeymanz on 2009-06-18
I think if you use the PUEL version of Virtualbox, you can let the guest control USB ports. Maybe you should run XP inside Ubuntu and try to use your MagicJack that way?

---

### Post by ZackM on 2009-06-18
Windows is harder on your system then Linux is, so running the virtual machine will be slower in comparison to Linux, which is lighter and faster.

---

### Post by longtom on 2009-06-18
> **ZackM said:**
> Windows is harder on your system then Linux is, so running the virtual machine will be slower in comparison to Linux, which is lighter and faster.

That makes a lot of sense.  We forget about the simple explainations to often...

---

### Post by Viva on 2009-06-18
> **zackm said:**
> windows is harder on your system then linux is, so running the virtual machine will be slower in comparison to linux, which is lighter and faster.

+1

---

### Post by aeiah on 2009-06-18
> **ZackM said:**
> Windows is harder on your system then Linux is, so running the virtual machine will be slower in comparison to Linux, which is lighter and faster.

yea but running windows with an ubuntu vm should in theory use the same resources as running linux with a windows vm. probably not the case though.

i believe kvm will allow you to forward usb ports onto the virtual machine quite easily, perhaps you could use that instead of virtualbox if virtualbox isnt up to scratch.

---

### Post by Johnsie on 2009-06-18
ummm.... maybe it's that Ubuntu runs crap inside a VM ;-)

---

### Post by ZackM on 2009-06-18
> **aeiah said:**
> yea but running windows with an ubuntu vm should in theory use the same resources as running linux with a windows vm. probably not the case though.


Not quite. When Windows is installed on your computer, it draws out more ram usage and CPU usage. When you run Ubuntu, it doesn't draw as much. That's what I stated above. When you run Windows as a virtual machine, however, it's using virtual memory and the program itself is using cpu and ram, and not the OS itself. That's why it runs smoother on Ubuntu than it does on Windows.

---

### Post by linsux on 2009-06-18
> **ZackM said:**
> Not quite. When Windows is installed on your computer, it draws out more ram usage and CPU usage. When you run Ubuntu, it doesn't draw as much. That's what I stated above. When you run Windows as a virtual machine, however, it's using virtual memory and the program itself is using cpu and ram, and not the OS itself. That's why it runs smoother on Ubuntu than it does on Windows.

Virtual Memory has to be from somewhere. You might be able to control the amount of RAM that XP eats with a VM, but the CPU is debatable. Personally, I think most of the logic in this thread is stupid. How much ram do you actually have? It shouldn't come down to what OS runs the other OS faster, it should come down to the OS you'll be using most.

I haven't found ANY real advantage to using VM in Linux as opposed to Windows.

---

### Post by starcraft.man on 2009-06-18
To be clear, what your saying is that when you run Windows natively and use it to host a Virtual Linux environment you notice terrible performance (i.e. dramatic drop, like 60 > 5 FPS) when compared to running the opposite scenario where Ubuntu/Linux is the native host and Windows is virtualized. I don't know why exactly it's happening (there could be many reasons), but I can assure you that Windows runs VMs well in my experience. I'm more inclined to believe it's some local problem to your specific situation. I've run both VirutalBox and VMWare workstation on several desktops in both situations and never seen an appreciable difference in performance once properly configured.

That's my 2 cents, I suggest you create a thread in one of the support sections and someone more knowledgeable than I can help you out.

---

### Post by FuturePilot on 2009-06-18
> **Simian Man said:**
> This is a *total* guess but Virtualbox on Linux installs two kernel modules.  Perhaps being able to add to the kernel gives it a performance benefit.  I have no idea how Vbox runs on Windows...

It does the same type of thing on Windows. It installs two drivers.

---

### Post by forrestcupp on 2009-06-18
The virtual memory argument isn't a good argument.  Virtual memory is just a portion of your RAM that is dedicated for a VM.  It works both ways.  When Windows is the host, you still dedicate a portion of your RAM for the virtual memory, so it shouldn't be affected.  If XP can run well in Ubuntu with 512 MB dedicated to virtual memory, then it can run the same with an actual 512 MB of available RAM.  That's not the problem.

My question to Swoll, did you remember to install vmWare tools?  That gives you a better virtual GPU and better virtual hardware support.  If you install vmware tools, it will speed things up significantly.  Tools comes with vmware Workstation, but if you google around, it's possible to get them installed in the free Player, too.

---

### Post by swoll1980 on 2009-06-18
> **forrestcupp said:**
> 
My question to Swoll, did you remember to install vmWare tools?  That gives you a better virtual GPU and better virtual hardware support.  If you install vmware tools, it will speed things up significantly.  Tools comes with vmware Workstation, but if you google around, it's possible to get them installed in the free Player, too.

Yeah I installed the tools. When I run it in Windows, or Ubuntu I allocate my 1 GB of RAM 50/50, so the guest, and the host both get 512 MB RAM, so in theory it should run smooth no matter which is the host, and which is the guest.

---

### Post by swoll1980 on 2009-06-18
> **Pogeymanz said:**
> I think if you use the PUEL version of Virtualbox, you can let the guest control USB ports. Maybe you should run XP inside Ubuntu and try to use your MagicJack that way?

I tried that. The magicjack is as finicky as it gets. It doesn't want to work when I do it that way.

---

### Post by raymondh on 2009-06-18
> **swoll1980 said:**
> I tried that. The magicjack is as finicky as it gets. It doesn't want to work when I do it that way.

swoll ... am thinkg about majicjack as well .... how is it affecting magicjack?

---

### Post by swoll1980 on 2009-06-18
> **raymondhenson said:**
> swoll ... am thinkg about majicjack as well .... how is it affecting magicjack?

If I use the magicjack in a Windows guest, I can make calls, people can hear me, but I can't hear them. I imagine that the incoming stream is being blocked, but I can't figure out how to fix it. If I run Windows nativity the magicjack works great! The clarity is better than a land line from the phone company, and for $19.99 you get unlimited local, long distance, call waiting, call forwarding, voice mail, E-mail notifications, 3 way calling, and caller id.

---

### Post by forrestcupp on 2009-06-18
> **swoll1980 said:**
> If I use the magicjack in a Windows guest, I can make calls, people can hear me, but I can't hear them. I imagine that the incoming stream is being blocked, but I can't figure out how to fix it. If I run Windows nativity the magicjack works great! The clarity is better than a land line from the phone company, and for $19.99 you get unlimited local, long distance, call waiting, call forwarding, voice mail, E-mail notifications, 3 way calling, and caller id.

My dad got MagicJack and he could make calls without any problem, but he couldn't receive calls.  When I tried to call his number, it went straight to his voicemail.  I don't know if he's gotten it fixed or not.

Have you been able to successfully receive calls?

---

### Post by swoll1980 on 2009-06-18
> **forrestcupp said:**
> My dad got MagicJack and he could make calls without any problem, but he couldn't receive calls.  When I tried to call his number, it went straight to his voicemail.  I don't know if he's gotten it fixed or not.

Have you been able to successfully receive calls?

Yes on a native Windows. Tell him to run magic fix, and if that doesn't work have him disable Windows firewall, and forward the ports to his router. He can get the port numbers from their website.

---

### Post by forrestcupp on 2009-06-18
what is magic fix?  I googled it and the only thing I could find was someone else suggesting to run magic fix.  Do you have a link?

---

### Post by raymondh on 2009-06-18
> **swoll1980 said:**
>  If I run Windows nativity the magicjack works great!

Hmmmm .... I don't have an extra machine just to run windows for majicjack.  I'll keep watching this thread for good news.

Thanks swoll..

---

### Post by swoll1980 on 2009-06-19
> **forrestcupp said:**
> what is magic fix?  I googled it and the only thing I could find was someone else suggesting to run magic fix.  Do you have a link?

The click here is the magicfix. Trouble shooting is on this page as well. [LINK]("magicjack.com/1/magicfix.asp")

---

### Post by forrestcupp on 2009-06-19
> **swoll1980 said:**
> The click here is the magicfix. Trouble shooting is on this page as well. [LINK]("magicjack.com/1/magicfix.asp")

Cool.  Thanks.  I saw that web page, but I didn't notice the "Click Here".

---

### Post by swoll1980 on 2009-06-23
Update: I got the magicjack working in a Windows guest, on an Ubuntu host Using vmware player. I created a Windows vm on my Windows vmware workstation. I copied the vm to my Ubuntu partition, and installed the Linux vmware player. It works fine. I don't know why it wouldn't work in vbox. vmware is a pain for me on Linux, but it was worth it.

---

