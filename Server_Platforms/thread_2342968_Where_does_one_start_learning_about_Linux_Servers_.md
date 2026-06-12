---
title: "Where does one start learning about Linux Servers and VPN's"
date: 2016-11-11
forum: Server Platforms
---

### Post by mikodo on 2016-11-11
Edit: Admins/Mods; Please, move this thread to an appropriate forum.

I like to read. I am not NOW actively setting up a server and wanting to use it to be accessed through a VPN. 

It seems there is so much information over my head and/or archaic within Linux. Sure, most older Linux documentation is still relevant today, but often if I go to a guide, the links to pages for explanations on the subjects are gone. Like what can be found, from [The Linux Documentation Project]("http://www.tldp.org/").  [Example]("http://www.losurs.org/docs/LDP/HOWTO/VPN-HOWTO/index.html") 

- If I can, (I mean have time to learn), when I buy/build a new tower machine for an Ubuntu server (or Debian) for housing multiple vm's, (GUI Desktops), I would like to refurbish and repurpose my old tower as as a data server, (Folders = Documents; Pictures; Music).

So, I need to learn, (explained to me like I was a two year old), how to setup a VPN to tunnel through with SSH traffic over the Internet, to my vm's to reach my data safely, on my server, (bidirectional).

Where to start learning for this with contemporary documentation, that is not meant to be for already technically educated people, (is that even possible?). 

Here is what I want to read, learn and document about, in a nutshell, (I think):

TOPICS

Server Installation 
Security
VPN
SSH
Hardware, (router, etc)

Any ideas where I should start? I am especially looking for recent documentation/guides/tutorials on _VPN, SSH_. I think the Server Installation, Security and Hardware, I can find relatively easily for my simple needs, but, I am always willing and able to read anything suggested on these too.

Thank you.

---

### Post by Kirk Schnable on 2016-11-12
Hello,

Just a few comments here for you.


> Server Installation 
Have you ever installed Ubuntu before?  It's not hard at all, it's not very different from installing Windows or any other operating system.  I doubt you will find much "documentation" on the installation process since it's fairly self explanatory.


> Security
Unfortunately this is a very vague thing to ask about and you most likely won't find any good documentation looking for it in these terms.  I would suggest you do some googling and reading on the following terms to learn more about security in Linux:
- iptables
- selinux
- file permissions


> VPN
What type of VPN are you looking to set up?  OpenVPN's documentation is actually very good in my opinion.
[https://openvpn.net/index.php/open-source/documentation.html](https://openvpn.net/index.php/open-source/documentation.html)

> SSH
SSH is pretty straight forward.  You connect, login, and get a terminal on the remote computer where you can run commands.  It's comparable to being on an Ubuntu machine with a GUI and opening up a terminal window.

But SSH can do a lot of cool stuff like key based authentication, X forwarding, TCP port forwarding; maybe you'll find this helpful:
[https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys](https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys)


> Hardware, (router, etc)
This is also pretty vague to be asking, and I'm not sure how it directly relates to Linux.

---

### Post by mikodo on 2016-11-12
> **Kirk Schnable said:**
>  - what you wrote in reply -

Thanks for the reply Kirk. I just looked back into the forums now and saw your reply. I feared my questions were too vague to be answered.

I have a couple of Xubuntu installs. I have been years with the Ubuntu family and I understand d-i/ubiquity well enough. I have been reading about Ubuntu and Debian server installs.

Your links on SSH && OpenVPN, are going to helpful and informative reading. 

I don't really know anything about 'Networking' and I am going to have to stumble my way around looking for topics to learn from on this.

Yes, security is a vague thing to ask about; Good advice with what you wrote. You are not first person to tell to learn about Linux file permissions. 

 
  Thank you.

---

### Post by Tadaen_Sylvermane on 2016-11-12
The first place I started with linux altogether and the source of my linux knowledge comes from using Virtualbox. I simulated and virtualized so many different things to learn everything I know now. That + googling and the sky is the limit. With virtualiing you can model and learn from it all from teh comfort of your main workstation.

---

### Post by SeijiSensei on 2016-11-12
One good resource is the Ubuntu Server Guide: [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

However the best way to learn is to take things one step at a time. Decide what you want to do first, learn what you need to know, then implement it.  Then move on to the next task.  

For VPNs, by far the simplest method is to use OpenVPN with a static, shared-key tunnel:  [http://openvpn.net/static.html](http://openvpn.net/static.html)  I have a number of these between my office and virtual servers hosted at [Linode](http://www.linode.com/) and among those servers as well.  Things are a bit trickier on 16.04 because of the switch to systemd, but I'm sure you can find documentation on that.

Ubuntu uses AppArmor rather than SELinux.  In general you don't need to worry about any of that if you stick to software in the Ubuntu repositories or in trusted PPAs.  On a server it is unlikely you would need to use a PPA to install standard server software like Apache, Postfix, PostgreSQL, MySQL, etc.  The standard repos are fine.

If you intend to have Internet-facing servers, then you should learn something about iptables and firewalling tools like [UFW](https://help.ubuntu.com/community/UFW).  Those are much more important than something like SELinux or AppArmor which are largely the preserve of the distribution packagers.

What you will have to get used to is relying on the terminal to manage everything rather than a GUI.  It's possible to install a GUI on the server edition, or to install the required server packages on a desktop version.  However in the long run you're going to want to become familiar with doing everything from the command prompt, especially if you intend to manage remote servers.

Good luck and have fun!

---

### Post by mikodo on 2016-11-12
> **SeijiSensei said:**
>  - place holder - 

Thank you, for your advice and the links you provided. 

I have long admired your experience and abilities with the stuff that you do with servers and networking; as seen from what I have read from your posts. I will try to follow your advice here. 

On enjoying myself, with cli and new ideas to attempt now. Tis strange how I have become bored, with not breaking much any more. ha!

Cheers!

---

### Post by JayKay3OOO on 2016-11-13
Don't limit yourself to Debian based linux though as many businesses (assuming you want a job for this) use red hat linux of which opensuse / fedora relate, suse more. 

Time and google. 

Only humans could invent boredom. :confused:

---

### Post by mikodo on 2016-11-13
^^ Oh, heavens no. I am only reading and wanting to learn to do what it is others' are doing, of which I know nothing of now. I will stick with Ubuntu for servers. As suggested to me earlier, the security of Ubuntu is what draws me here. I would like to play with Debian installs again, to learn more of administering an install through within 'the Debian way' of which I am fond of. Probably in vm's. That could only 'enhance' my knowledge of administering Ubuntu installs. Not a complete waste of time spent and energy expended, in my way of thinking.

Thanks.

---

### Post by SeijiSensei on 2016-11-15
I'd give CentOS a try next rather than Debian to see how things are done in the RedHat-flavored world.  Like JayKay said, if you're thinking about working as a systems administrator, you're going to encounter a lot more people using RedHat and its clones in commercial settings.

> I have long admired your experience and abilities with the stuff that you do with servers and networking; as seen from what I have read from your posts. I will try to follow your advice here.
(blushes) Aww, gosh.

---

### Post by mikodo on 2016-11-16
> **SeijiSensei said:**
>  - snip - if you're thinking about working as a systems administrator
Hi again.

No chance of that for me. I am too old now. (I am retiring from my professional life). I only want to read, learn, and possibly do some of the things of which I have read others, including yourself, are doing. 

Some of the best advice offered for soon to be retirees, is to have things to do that interest them in retirement. Like hobbies, community and social involvement including family, (especially for we people who have spent our lives focusing on work, to the sacrifice of these other things). I know that learning of these technical things are a hobby I enjoy. 

Thing is, as we age in our lives, we all will have approaching senile dementia in greater degrees, the longer we live. The bodily 'systems', including the 'nervous system', are and will continue to be in declines of functional abilities. I know that a career now in this is not possible, and in reality, not wanted. But, that doesn't mean that approaching old age and old age has to 'suck', given the opportunities it presents one in retirement, that wasn't available to them earlier in life. 

Obviously, I am thinking about these things now, and being here helps me to pursue, what pleases me.

Thank you.

---

### Post by SeijiSensei on 2016-11-16
Hey, I'll be 67 in a couple of days, so I understand.  I often say I have skill set of a 30-year-old in a body that makes me unemployable in the IT world.

I've wondered whether there would be interest in a class about Linux for seniors.  The usual offerings at our Senior Center focus on Windows and Macs, but many older people have fairly limited computing needs that Linux supports well and cheaply, especially on older hardware.  On the other hand, Linux has a higher initial learning curve compared to buying a machine with a pre-installed copy of Windows or OSX, so the audience is likely not that large.

---

### Post by bearlake on 2016-11-17
> **SeijiSensei said:**
> Hey, I'll be 67 in a couple of days, so I understand.  I often say I have skill set of a 30-year-old in a body that makes me unemployable in the IT world.

I've wondered whether there would be interest in a class about Linux for seniors.  The usual offerings at our Senior Center focus on Windows and Macs, but many older people have fairly limited computing needs that Linux supports well and cheaply, especially on older hardware.  On the other hand, Linux has a higher initial learning curve compared to buying a machine with a pre-installed copy of Windows or OSX, so the audience is likely not that large.

Hi SeijiSensei, looking at your picture I would say your not a day over 30! :-$

Tagging myself to this thread as I'll been doing the same as the OP shortly.

The info you provided in this thread is just priceless.

I'll be sure to start my own thread if questions arise.

Thanks!

---

### Post by SeijiSensei on 2016-11-17
> **bearlake said:**
> Hi SeijiSensei, looking at your picture I would say your not a day over 30! :-$
Actually the guy in that picture is [immortal]("https://en.wikipedia.org/wiki/List_of_Twelve_Kingdoms_characters#Shoryu")!  He's gazing at a nearby brothel he frequents and no doubt imagining the women he's been with who are no long alive.

---

