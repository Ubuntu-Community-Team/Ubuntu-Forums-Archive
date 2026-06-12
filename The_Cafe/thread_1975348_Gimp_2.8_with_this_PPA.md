---
title: "Gimp 2.8 with this PPA"
date: 2012-05-07
forum: The Cafe
---

### Post by sdowney717 on 2012-05-07
> sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update && sudo apt-get install gimp

[http://omgubuntu.co.uk/2012/05/gimp-2-8-released/](http://omgubuntu.co.uk/2012/05/gimp-2-8-released/)

single window mode is under the window menu.

Running it on Precise and it works.

---

### Post by neu5eeCh on 2012-05-07
Don't install it from the PPA... yet... if anyone is running 11.10. There still appear to be some unresolved dependency issues. If you *add-apt-repository*, you will get the warning. 

Also, look [here]("https://launchpad.net/%7Eotto-kesselgulasch/+archive/gimp"), and keep checking in.

---

### Post by forrestcupp on 2012-05-07
> **VTPoet said:**
> Don't install it from the PPA... yet... if anyone is running 11.10. There still appear to be some unresolved dependency issues. If you *add-apt-repository*, you will get the warning. 

Also, look [here]("https://launchpad.net/%7Eotto-kesselgulasch/+archive/gimp"), and keep checking in.

They've had some problems with 11.10, but it works just fine in 12.04. Maybe they'll get it in the Backports soon.

---

### Post by Hylas de Niall on 2012-05-07
Yep. It's running great for me in 12.04 :)

---

### Post by bluelord_ro on 2012-05-07
Hy,
In my Software center appear v2.6 if i use the ppa it dont make the upgrade, i still have v2.6.

---

### Post by otto06217 on 2012-05-07
> **VTPoet said:**
> Don't install it from the PPA... yet... if anyone is running 11.10. There still appear to be some unresolved dependency issues. If you *add-apt-repository*, you will get the warning. 

Also, look [here]("https://launchpad.net/%7Eotto-kesselgulasch/+archive/gimp"), and keep checking in.

Hi, I'm the maintainer of this PPA. There's a lot of dependency issues. I think about to remove the Oneiric packages.

Not yet, but my problem is the lack of time testing the packages for all the Oneirics including Mint 12.

If you have a testing system feel free to test it but don't do so on your production environment. I'll really not responsible for damaging your system.

Cheers

Thorsten "Otto" Stettin

---

### Post by otto06217 on 2012-05-07
> **Hylas de Niall said:**
> Yep. It's running great for me in 12.04 :)

Yes, we can!:P

But on Oneiric it's a dependency nightmare.

I think there's a lot of work on Oneiric.:confused:

Cheers

The Maintainer

---

### Post by Primefalcon on 2012-05-07
Upgrade to precise, its now the current version and the current LTS version and will be supported for 5 years

---

### Post by forrestcupp on 2012-05-07
> **bluelord_ro said:**
> Hy,
In my Software center appear v2.6 if i use the ppa it dont make the upgrade, i still have v2.6.
If you aren't running 12.04, it's not going to work anyway. But if you are running Ubuntu 12.04, try typing this in a console, then check the Software Center again:
```
sudo apt-get update
```

---

### Post by BrokenKingpin on 2012-05-08
Single window mode looks awesome. I have used Gimp for years and tolerated the split windows, but I always found it a bit annoying to use.

---

### Post by mips on 2012-05-08
> **BrokenKingpin said:**
> Single window mode looks awesome. I have used Gimp for years and tolerated the split windows, but I always found it a bit annoying to use.

The split view works very well for people with dual monitors.

---

### Post by ajgreeny on 2012-05-08
> **mips said:**
> The split view works very well for people with dual monitors.
And on my non-widescreen display I prefer the separate windows.  At least this is an option, so others can have their preference and I can have mine.

---

### Post by sefs on 2012-05-08
Will this upgrade ever occur in the regular repos for Precise?

---

### Post by forrestcupp on 2012-05-08
> **mips said:**
> The split view works very well for people with dual monitors.
That's why it's good that they made it an option that is easily changed.

---

### Post by PayPaul on 2012-05-08
Yeah, Gimp is OK but it still doesn't have adjustment layers. A serious drawback for me.

:sad:

---

### Post by mips on 2012-05-09
> **PayPaul said:**
> Yeah, Gimp is OK but it still doesn't have adjustment layers. A serious drawback for me.


Coming in v3 I think.

---

### Post by Artemis3 on 2012-05-11
Skipping the single window stuff, anyone knows if they fixed the "tear menus" so they remain showing on the desktop and still work?

---

### Post by PayPaul on 2012-05-28
> **mips said:**
> Coming in v3 I think.

How long has GIMP been in circulation? I'd like to see whether the developers are serious about making it a serious competitor. The one thing that I've found with Linux based OS's is that they are OSBC, Operating Systems By Committee. Why should I upgrade to 12.04 just to get one program working properly? We all know how difficult it is to get anything long term accomplished by committees. Look at the US Congress.:(

---

### Post by thatguruguy on 2012-05-28
> **PayPaul said:**
> Why should I upgrade to 12.04 just to get one program working properly?

Did anyone tell you that you should upgrade to 12.04 solely to take advantage of the Gimp 2.8 ppa?  If so, where was this suggestion made?

---

### Post by mips on 2012-05-28
> **PayPaul said:**
> Why should I upgrade to 12.04 just to get one program working properly? We all know how difficult it is to get anything long term accomplished by committees.

Dependency issues. Ever noticed in the windows world where companies no longer support older versions of windows for their new products? (Same applies to OS X)

Someone might backport it to older versions though.

---

### Post by Lucradia on 2012-05-28
I really don't like The GIMP now that I can't use CTRL[+SHIFT]+S to save anything other than XCF.

I'll stay with 2.6. If I have to upgrade, I'll just try to find another editor or somehow figure out how to downgrade while still keeping the current version of GTK (Pidgin.)

---

### Post by PayPaul on 2012-05-28
> **mips said:**
> Dependency issues. Ever noticed in the windows world where companies no longer support older versions of windows for their new products? (Same applies to OS X)

Someone might backport it to older versions though.

Yes, I'm very aware of that. However most major programs made for that other OS will work with a subsequent release of that OS. GIMP, in spite of its flaws, is a major graphics program for Linux and Ubuntu. I do understand a bit about dependencies. They remind me a bit of .dll files. There are, I believe, a number of programs in Linux that rely upon the same apps or dependencies. Are the dependencies or their configurations for this latest version so special to the latest LTS of Ubuntu? Was it created only using Pangolin as a base?

---

### Post by buzzingrobot on 2012-05-28
> **PayPaul said:**
>  Are the dependencies or their configurations for this latest version so special to the latest LTS of Ubuntu? Was it created only using Pangolin as a base?

No.

To over simplify, applications depend on libraries of compiled code (often, a .dll in Windows) to supply their underlying functionality. When Gimp opens a file,  for example, it is library code that it's using. 

Code libraries get updated for the same reason as applications:  To fix bugs, add more capabilities, address new hardware. Often, those changes make it difficult or impossible or not worth spending resources on to insure the new code is backwards compatible with everything that's been written previously. The effect of this is, perhaps, less apparent in the Windows world because Microsoft has a financial incentive to maintain backwards compatibility as much as possible, and because vendors have a financial reason to write Windows drivers for their products that are equally compatible.  Even there, though, limits to compatibility exist.

Gimp, then, was coded on a certain set of libraries. If those libraries are not present on a system, they need to be installed before 2.8 will work.  Problems arise when the newer libraries are not compatible with other software already on the system. Someone may back port it, i.e., find a way to compile it on 12.04.

---

### Post by PayPaul on 2012-05-28
I may still do an upgrade to Precise but need to find a way to get to the Classic Gnome shell. That's another ball of wax for which I'll no doubt discover the solution on this forum somewhere. I still stand by my desire/NEED to have adjustment layers. 

The one thing that got my respect for Gimp was how it was so much easier to use the Pen selection tool in it. Other aspects of it are rather clumsy and require more steps than are desirable. For example the painting of selection areas. I'm not sure if having all the selection parameters on the side panel is helpful. There are a few more parameters available though so I'll give it a 7 in terms of the benefits of that tool. GIMP serves a purpose for simple editing but for some of the more complicated work I do it falls short. If the new release or some near future release would allow for 8bf plugins and adjustment layers I'd be very happy to switch to it full time.

---

### Post by gingermark on 2012-06-03
I'm running a fresh 12.04 install and installed 2.6 with a gimpload of plugins from the repositories. Anyone know if 2.6 plugins are likely to still work if I upgrade to 2.8?

Thanks.

---

