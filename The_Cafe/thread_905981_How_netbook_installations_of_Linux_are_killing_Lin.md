---
title: "How netbook installations of Linux are killing Linux"
date: 2008-08-30
forum: The Cafe
---

### Post by Ellipsis on 2008-08-30
(please note that I can not speak for all netbook linux installations but I am guessing that all have some of the problems that I discuss below)

I recently bought an Aspire One netbook and frankly the installation of Linux on it is absurd. Linpus is an "ok" distribution by itself but the pre-installed extras are what bug me. Their media player. photo player and even the "basic" menu all feel cheap and flimsy. Why in their right minds would they spend any money buying/developing these things when there are so many better solutions available. Moreover, they limit features like the package manager to hidden away advanced mode. What was Acer thinking? 

I have now a regular on the Aspire One user forums and what I have noticed is disappointing and contributing to the problem. The experienced Linux users are "fleeing" to better pre-set distributions/software packages and the new Linux users are being left with little or no help. Many are thus choosing to return their linux version for a windows pre-installed ONE. 

I honestly can not blame these people because what they are getting is not the Linux I love.

---

### Post by starcannon on 2008-08-30
They are selling a device not an os.

They want tech support fees at an absolute minimum, so hiding the tools that cause the problems makes sense from a business standpoint. 

I actually think the umpc's(netbooks) are good for linux. People see what linux can do on one of these little notebooks, and are exposed to what it feels like to live life without viruses, and perhaps start shopping for linux on their next Desktop or Laptop.

/shrug, guess its really all a matter of perception. But I don't think umpc's are hurting us; though, I can see the plausibility of your argument.

---

### Post by aysiu on 2008-08-30
If a netbook comes out with Ubuntu Netbook Remix that boots in seconds and isn't too far from vanilla Ubuntu (i.e., all repositories work, all Ubuntu tutorials apply), then I think Netbooks could be good.

I have to say Xandros gave a lot of new Eee PC users a bad first impression of Linux. Linux already has a bad enough reputation as far as software installation goes, but Xandros makes the reputation even worse. Its "security" is also worse than Windows XP's default to administrator (single-user, always with the username *user*, and inability to have a functional system unless no password is ever asked for for *sudo* commands).

I've installed Ubuntu on the Eee and love it... except for the slow boot times.

---

### Post by Ellipsis on 2008-08-30
> **starcannon said:**
> They are selling a device not an os.

They want tech support fees at an absolute minimum, so hiding the tools that cause the problems makes sense from a business standpoint. 

I actually think the umpc's(netbooks) are good for linux. People see what linux can do on one of these little notebooks, and are exposed to what it feels like to live life without viruses, and perhaps start shopping for linux on their next Desktop or Laptop.

/shrug, guess its really all a matter of perception. But I don't think umpc's are hurting us; though, I can see the plausibility of your argument.

I understand what you are saying but not having/hiding the Add/Remove software tool is a bad decision. Many people fumble around with software first before seeking help online. For example they might try installing from unreliable software packages first and that would give them/tech support a bigger headache.

Other normal expected things such as desktop customization can not possibly cause that many problems. Changing your desktop icons should not be a matter of going into a configuration file.

---

### Post by aysiu on 2008-08-30
It's okay to hide functionality. It is not okay to take functionality away.

I don't know about the Acer Aspire One, but I really feel that Asus has crippled Xandros for the Eee. It isn't the simplified interface (I think that interface is great for new users, actually, and the advanced interface can be switched to quite easily). It's the lack of security and easy software installation. No software in the repositories. No easy way to add new users or set up different levels of privilege.

---

### Post by Bachstelze on 2008-08-30
> **aysiu said:**
> It's okay to hide functionality. It is not okay to take functionality away.

Amen to that. And sadly, netbook installations is not the only domain where it applies...

---

### Post by crimesaucer on 2008-08-30
I see your point... but I still want one of these 64 bit netbooks with a x86_64 bit version of Arch or AMD64 Gentoo using xfce4.....

[http://jkkmobile.blogspot.com/2008/06/amd-joins-netbook-race-with-low-cost.html](http://jkkmobile.blogspot.com/2008/06/amd-joins-netbook-race-with-low-cost.html)

---

### Post by Bachstelze on 2008-08-30
I really wouldn't run Gentoo on somethink like this. All the compiling will kill it (unless you have another machine to distcc, of course).

---

### Post by crimesaucer on 2008-08-30
> **HymnToLife said:**
> I really wouldn't run Gentoo on somethink like this. All the compiling will kill it (unless you have another machine to distcc, of course).

Why? an AMD Turion 64x2 with 1GB ram... seems like if it was running a lightweight distro and a wm like xfce4 that it would be perfect for compiling.

... I probably would just do what I do now which is to use Arch and a compiled gentoo zenmm kernel for AMD64...


That way I get the nice zenmm kernel for AMD and get to use pacman as a package manager for easy updates... and AUR/ABS makepkgs are super fast.


... but it would be nice to compile every app to be as fast as possible on Gentoo...

---

### Post by Bachstelze on 2008-08-30
> **crimesaucer said:**
> Why? an AMD Turion 64x2 with 1GB ram... seems like if it was running a lightweight distro and a wm like xfce4 that it would be perfect for compiling.

Yeah, but on something that small, you can bet the airflow won't be great, so it will surely overheat a lot.

And really, the fact that compiling makes things run faster is a myth. Compiling has many advantages over precompiled packages, but this is not one of them.

---

### Post by malspa on 2008-08-31
[http://www.linesign.ca/082708-Netbooks](http://www.linesign.ca/082708-Netbooks)

Probably not the best way to get into Linux.

Not "killing Linux," though.

---

### Post by Colro on 2008-08-31
I actually just ordered an EEE 1000H (with windows; the linux version is $100 more...). It's going to take me quite awhile to get all of the hardware quirks out if I choose debian or ubuntu for it, but at least it'll be a usable operating system -- Asus's Xandros is absolutely terrible.

---

### Post by crimesaucer on 2008-08-31
> **HymnToLife said:**
> ... you can bet the airflow won't be great, so it will surely overheat a lot.

And really, the fact that compiling makes things run faster is a myth. Compiling has many advantages over precompiled packages, but this is not one of them.

Well... I'm not too sure about what is myth or not... but ever since I started using a kernel that I compiled with all AMD64 settings instead of the generic x86_64 settings, I have seen an improvement in speed. I also have fixed a couple of errors that I would see in my old dmesg using the generic Arch kernel (which was already fast).


I'm not sure what individual packages compiled with the correct cflags would be like, but it's mentioned a lot in the gentoo wiki and it sounds like it would be faster... I figure that you never actually know until you try something yourself...


As for it overheating... that might be a problem... but I do have one of those 2 fan aluminum laptop coolers that helps cool things down a bunch.


... and if gentoo is a hassle, then there is always Arch and xubuntu for lightweight distros with solid repositories that don't need compiling.

---

### Post by youngalfred on 2008-08-31
I dont think that netbooks are killing linux. i am the proud owner of an eeepc 701 and i tell everyone.  sure Xandros may have some annoying things about it (like that damned wireless... no dhcp offers?)  but for the average person it works, and is simple.  I believe that Asus were very clever in designing some parts of Xandros such as the uber-quck boot time and the unionfs (i mean, how easy is it to press f2 at boot 2 restore to defaults?)  and if you aren't the average user, Asus provides all the divers to work on other OS's.  I'm running ubuntu now and the only complaint is the boot time.  One other reason why I love the netbook is because it has standard hardware, which means everyone knows what you are running, and what bugs occur. when I installed ubuntu on the eee all I had to do was go to the eeeuser.com wiki and there is a script their that automatically sets everything up, and has details if you want to do it manually.  Its awesome :)

---

### Post by Vadi on 2008-08-31
From what I read, Ubuntu's Netbook Remix received praise when the hardware didn't much (it was in Sylvania's case. In Dell's case, it was just praised). So it depends on the quality of the OS...

---

### Post by joninkrakow on 2008-08-31
> **aysiu said:**
> 

...but Xandros makes the reputation even worse. Its "security" is also worse than Windows XP's default to administrator (single-user, always with the username *user*, and inability to have a functional system unless no password is ever asked for for *sudo* commands).


In what concrete way is the security worse? Please share specifics as to exploits, and genuine, practical exploitability on the eeeePC. How is the eee so insecure? I have tried to crack into my wife's eeePC, and have not yet succeeded. There are no known exploits that could take advantage of the Xandros system running on the eeePC. Xandros is not Windows, and it is not likely to suffer the same fate. Beyond that, because it's a netbook, it is not likely to be used in the same place long enough to be exploited, and even if it were possible, for instance, at our local mall. Once my wife disconnects, it's gone--and it doesn't contain much, if any information that a cracker would want--these are _netbooks_ not laptops, not desktops. In their intended use, they just don't have any genuine risks that I can see, so I think it's a fair quesiton. What specific, genuine problems have you experienced with your eee, or are you aware of? 

BTW, the developer of Puppy Linux has written extensively on this subject, and has made a lot of valid arguments that are valid as well for the eeePC. Worth reading.


as to the repos, have you tried an apt-cache search? There are some interesting goodies in the repos, without enabling the extra ones, and bothering to "pin" and such. Not tons, but some interesting stuff, nonetheless. Again, the purpose of the netbook is just that--browsing the net, and doing some light email.... nothing more. Everything else is icing on the cake. That is what the eee was intended for. In that capacity, with the original OS, it's capital!
-Jon

---

### Post by pHr34kY on 2008-08-31
I've played with a few netbook distros before, including the EeePC and Aspire One. I've also tried the Ubuntu netbook remix on my home laptop.

I must say, the EeePC scares away both newbies and l33t hax0rz alike. I've seen people in-store get frustrated and walk away within seconds. I was annoyed at the fact that I had to search a web forum to find out how to open a console.

I really, really hope that Mark can push Ubuntu Netbook remix. It is far superior to what Asus and Acer have to offer, and the support is much better. Not to mention that Canonical's support desk will grow exponentially (which I believe is their main source of sustainable income) if they can onsell (i.e bundle) support with their product. It would also help manufacturers because their machines would actually have more appeal than a price tag, and they'll surely ship more units. Not to mention making their in-house distro development team redundant.

The current distros are a very bad introduction to Linux.

Oh, and prepare to get [dugg]("http://digg.com/linux_unix/How_netbook_installations_of_Linux_are_killing_Linux")!

---

### Post by crimesaucer on 2008-09-01
> **pHr34kY said:**
> 
Oh, and prepare to get [dugg]("http://digg.com/linux_unix/How_netbook_installations_of_Linux_are_killing_Linux")!

Great, now I get to read about how much of an idiot I am.



You suggest ubuntu, but I think it would be better to use xubuntu with xfce4, it looks better, would be faster and lighter, and has compositing.

---

### Post by starcannon on 2008-09-01
> **Colro said:**
> I actually just ordered an EEE 1000H (with windows; the linux version is $100 more...). It's going to take me quite awhile to get all of the hardware quirks out if I choose debian or ubuntu for it, but at least it'll be a usable operating system -- Asus's Xandros is absolutely terrible.

The Linux version has a larger SSD, likely a great deal of the cost increase.

---

