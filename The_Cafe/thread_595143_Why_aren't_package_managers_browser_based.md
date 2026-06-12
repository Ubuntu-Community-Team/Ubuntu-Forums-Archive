---
title: "Why aren't package managers browser based?"
date: 2007-10-28
forum: The Cafe
---

### Post by Palmyra on 2007-10-28
No, I am not talking about the direction much of computing is going in (moving to browser based applications).  I am talking about directly accessing package managers via a standard browser.  

Here's why.

1.  It makes no sense to maintain an separate application for managing packages when browsers are fully capable of doing this.  Have a homepage much like Google, search for the package, and download the package you find.  It is a very simple and intuitive design (if designed right).  

2.  Notice how Epiphany uses less resources than Synaptic?  Another bonus.

3.  Epiphany is one of Gnome's default applications.  Synaptic is not a DE-specific application.

4.  Browsers are universal.  Regardless of which operating system you come from, the design of a browser is so familiar, you can get to work right away.  You know where all the buttons are.  If you are a previous Windows user, you remember that you got your applications from websites like Download.com.  Instead of browsing to a website, all your search features and all other features provided by package managers are directly integrated into the browser.

5.  Browsers are maintained by an external group, and are regularly updated.  I don't recall the last update Synaptic has had. 

5.  Reduce the need for multiple applications when one application can take care of both Internet browsing as well as functioning as a package manager.  Clutter is reduced as well.  

6.  To possibly support Ubuntu's progress, ads can be placed next to search results.  Please do not be selfish: you've gotten an operating system entirely for free, you pay absolutely nothing; the least you can do is view several text-based ads that could help Ubuntu.  Again, don't be selfish.  No one likes ads, but this is for a good cause.  This is JUST AN IDEA.  

You all can add more ideas, and I am sure there are cons, but I am just throwing around ideas.  I already know Conary is browser-based, but Ubuntu does not use Conary.

---

### Post by ahaslam on 2007-10-28
Have you tried Foresight Linux?
[http://www.foresightlinux.org/screenshots/view/fsm/](http://www.foresightlinux.org/screenshots/view/fsm/)

---

### Post by -grubby on 2007-10-28
> **Palmyra said:**
> 
3.  Epiphany is one of Gnome's default applications.  Synaptic is not a DE-specific application.


that's an advantage (for synaptic)

---

### Post by saulgoode on 2007-10-28
> **Palmyra said:**
> 1.  It makes no sense to maintain an separate application for managing packages when browsers are fully capable of doing this. 

Packages and package management is specific to a particular distribution. Browsers are cross-distro, if not cross-platform. Why would a Slackware/RedHat/Windows/... user want to have his browser contain support for Ubuntu system maintenance? Why would the browser developers (who might be using Slackware/RedHat/Windows/...) wish to maintain Ubuntu-specific code?

If there were an Ubuntu-only browser then, yes, that browser might very well include support for package maintenance. But Ubuntu would be on its own to develop that browser -- again, other distros wouldn't be interested maintaining Ubuntu-specific code.

---

### Post by HermanAB on 2007-10-28
Uhmmm, most every package repository can be accessed online via a browser.  So I don't quite get your complaint.  If you like to use a browser for installing packages - go ahead - there is nothing stopping you, except maybe if you don't know how to use Google to find them.

---

### Post by Henaro on 2007-10-28
Why don't we just all move to the terminal.  

1.  Eats up less RAM.
2.  Everyone has one.
3.  No messy GUIs.
4.  No matter which operating system you come from, the design is so familiar!  


;)

---

### Post by SunnyRabbiera on 2007-10-28
> **nathangrubb said:**
> that's an advantage (for synaptic)

I agree, as Epiphany is a mainly gnome app.

anyhow we do have something on both debian and ubuntu thats comes close to the original posters idea:

[The Ubuntu package page]("http://packages.ubuntu.com/")

the debian one:
[here]("http://www.debian.org/distrib/packages")

then there is getdeb too:
[getdeb]("http://www.getdeb.net/")

the thing is that the smaller distributions such as Mepis, PCLinux and a few others rely on FTP mirrors as opposed to http ones.
This is mainly because from my understanding it is easier to mirror a ftp directory then a HTML one.
From what I have discovered that to save space on servers the smaller distributions archive all the directories and files in a large ZIP where both binary and source packages are held.
Ubuntu still does this too so that the directories could be mirrored despite it having a package page like I listed above.
the smaller distros i know cannot afford such a page but ubuntu can, however i know they keep to the other methods probably to make sure everything holds together.

---

### Post by ice60 on 2007-10-28
i installed a package on a web page with gutsy the other day, i just clicked on the page and apt installed it :D it might be called apturl :confused: one of the bsd's does it too.

[http://ubuntu-tutorials.com/2007/10/23/apturl-web-based-package-installation/](http://ubuntu-tutorials.com/2007/10/23/apturl-web-based-package-installation/)

i'm using suse atm, but see if this works. it might install ubuntu-restricted-extras -
[click this](apt:ubuntu-restricted-extras)

EDIT. actually this is a better one to try, elinks, it's a texted browser with more features then other texted browsers. i've no idea if it will work though??
[click](apt:elinks)

---

### Post by Polygon on 2007-10-28
but usually the design philophsy with linux programs is that it does one thing, and it does it well. So, having 50 million things integrated into just the web browser doesnt really work

synaptic is meant to browse/install/uninstall/upgrade the repos and packages. thats it.

there is nothing stopping someone making a program that makes it so you can browse the repos using a web browser, but there is no reason to really use a web browser unless your doing it remotely...and even then you could use the terminal.

---

### Post by ubuntu27 on 2007-10-28
Well.. it's not exactly what the OP wanted, but there is a website called [Ubuntu Packages]("http://packages.ubuntu.com/") in which you can download individual packges that are in the resporitories with your **browser**

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by boast on 2007-10-28
you mean something like packages.debian.org but instead of having to download the deb, and then install it, theres something to pick up the deb and auto install it?

 Like clicking a link for an itunes song via web browser automatically opens itunes via itms://*link*

---

### Post by HermanAB on 2007-10-28
Exactly, go there with for example Konqueror and double click the file - La voila.

---

### Post by ice60 on 2007-10-29
gutsy has it installed on a default install, and older ubuntu versions have it in the repos, although i think it only works with firefox! i tried clicking on the page with opera and it didn't work, but clicking the link with firefox installed the package.

---

### Post by BDNiner on 2007-10-29
My only problem with this is that you could easily be spoofed into giving away your root password. i like having a package manager and i feel synaptic does its job well.

---

### Post by ice60 on 2007-10-29
suse does it too, 10.3 comes with the package preinstalled, and here's the package for 10.2 users, called yast2-metapackage-handler-0.5.2-3.1.noarch.rpm -
[http://download.opensuse.org/repositories/openSUSE:/Tools/openSUSE_10.2/noarch/](http://download.opensuse.org/repositories/openSUSE:/Tools/openSUSE_10.2/noarch/)

edit, you need perl-XML-XPath-1.13-2.1.i586.rpm from this link too -
[http://download.opensuse.org/repositories/openSUSE:/Tools/openSUSE_10.2/i586/](http://download.opensuse.org/repositories/openSUSE:/Tools/openSUSE_10.2/i586/)

it adds the repos automatically then installs all the dependencies and packages you need, all from one click on a web page!

---

### Post by Wiebelhaus on 2007-10-29
> **ahaslam said:**
> Have you tried Foresight Linux?
[http://www.foresightlinux.org/screenshots/view/fsm/](http://www.foresightlinux.org/screenshots/view/fsm/)

That's a really nice OS but man does that package manager craters horribly on me , I couldn't get the darn thing to install or even remove anything , much improvement needed.


And that's precisely WHY I disagree with browser based  package management.

---

### Post by Incense on 2007-10-29
I think that's the whole idea behind CNR. You just browse the packages online, click and it installs. I think you can even use it with Ubuntu now.

[http://www.cnr.com/index.seam]("http://www.cnr.com/index.seam")

---

### Post by RAV TUX on 2007-10-29
> **Palmyra said:**
> No, I am not talking about the direction much of computing is going in (moving to browser based applications).  I am talking about directly accessing package managers via a standard browser.  

Here's why.

1.  It makes no sense to maintain an separate application for managing packages when browsers are fully capable of doing this.  Have a homepage much like Google, search for the package, and download the package you find.  It is a very simple and intuitive design (if designed right).  

2.  Notice how Epiphany uses less resources than Synaptic?  Another bonus.

3.  Epiphany is one of Gnome's default applications.  Synaptic is not a DE-specific application.

4.  Browsers are universal.  Regardless of which operating system you come from, the design of a browser is so familiar, you can get to work right away.  You know where all the buttons are.  If you are a previous Windows user, you remember that you got your applications from websites like Download.com.  Instead of browsing to a website, all your search features and all other features provided by package managers are directly integrated into the browser.

5.  Browsers are maintained by an external group, and are regularly updated.  I don't recall the last update Synaptic has had. 

5.  Reduce the need for multiple applications when one application can take care of both Internet browsing as well as functioning as a package manager.  Clutter is reduced as well.  

6.  To possibly support Ubuntu's progress, ads can be placed next to search results.  Please do not be selfish: you've gotten an operating system entirely for free, you pay absolutely nothing; the least you can do is view several text-based ads that could help Ubuntu.  Again, don't be selfish.  No one likes ads, but this is for a good cause.  This is JUST AN IDEA.  

You all can add more ideas, and I am sure there are cons, but I am just throwing around ideas.  I already know Conary is browser-based, but Ubuntu does not use Conary.

Who needs browser based package managers when you can just click a link here in this thread to install things (using Gutsy & Firefox):

example:

[apt:songbird](apt:songbird)

[apt:k3b](apt:k3b)

---

### Post by S3Indiana on 2007-10-29
> **RAV TUX said:**
> Who needs browser based package managers when you can just click a link here in this thread to install things (using Gutsy & Firefox):

example:

[apt:songbird](apt:songbird)

[apt:k3b](apt:k3b)Two problems with that method: First you have to know what the package name is (IOW that it exists), and Second what are the alternatives to that package??? [CNR.com]("http://www.cnr.com") solves both problems...

---

### Post by RAV TUX on 2007-10-29
> **S3Indiana said:**
> Two problems with that method: First you have to know what the package name is (IOW that it exists), and Second what are the alternatives to that package??? [CNR.com]("http://www.cnr.com") solves both problems...So does Google.

---

### Post by S3Indiana on 2007-11-06
> **RAV TUX said:**
> [quote=S3Indiana;3666252]Two problems with that method: First you have to know what the package name is (IOW that it exists), and Second what are the alternatives to that package??? [CNR.com]("http://www.cnr.com/") solves both problems...
So does Google.[/quote]How does Google solve not knowing the package name in the first place???

---

### Post by S3Indiana on 2007-12-01
> **S3Indiana said:**
> [CNR.com]("http://www.cnr.com") solves both problems...[CNR.com]("http://www.cnr.com/") has been updated including a client [upgrade]("http://www.cnr.com/supportPages/aboutDownloadPlugin.seam") supporting 7.04 & 7.10 (also visit the [CNR Community]("http://community.cnr.com/index.jspa"))...

---

### Post by Mateo on 2007-12-01
It's possible but doesn't seem easy.  Synaptic doesn't just install applications from the internet.  It also can use CDROMs.  How do you do that in a web application?

What about 3rd party Repos?  How do you handle those?  Will this web application use your sources.list?  Is it possible to give a web application root access (assuming Epiphany or Firefox or whatever is NOT running in root)?

And if so, it also needs to be able to edit your sources.list, since Synaptic can do that too.

---

### Post by S3Indiana on 2007-12-01
> **Mateo said:**
> It's possible but doesn't seem easy. 

What about 3rd party Repos?  How do you handle those?  Will this web application use your sources.list?  Is it possible to give a web application root access (assuming Epiphany or Firefox or whatever is NOT running in root)?

And if so, it also needs to be able to edit your sources.list, since Synaptic can do that too.The design of[ CNR.com]("http://www.cnr.com") is for the request to be initiated from the web site, but the download and installation occurs from a client on the host machine (which has the appropriate permissions to install packages)...

---

### Post by IYY on 2007-12-02
I don't even bother loading synaptic up. Seriously, is it that difficult to type

```
apt-cache search appname
sudo apt-get install appname
```

---

### Post by RAV TUX on 2007-12-02
> **Palmyra said:**
> No, I am not talking about the direction much of computing is going in (moving to browser based applications).  I am talking about directly accessing package managers via a standard browser.  

Here's why.

1.  It makes no sense to maintain an separate application for managing packages when browsers are fully capable of doing this.  Have a homepage much like Google, search for the package, and download the package you find.  It is a very simple and intuitive design (if designed right).  

2.  Notice how Epiphany uses less resources than Synaptic?  Another bonus.

3.  Epiphany is one of Gnome's default applications.  Synaptic is not a DE-specific application.

4.  Browsers are universal.  Regardless of which operating system you come from, the design of a browser is so familiar, you can get to work right away.  You know where all the buttons are.  If you are a previous Windows user, you remember that you got your applications from websites like Download.com.  Instead of browsing to a website, all your search features and all other features provided by package managers are directly integrated into the browser.

5.  Browsers are maintained by an external group, and are regularly updated.  I don't recall the last update Synaptic has had. 

5.  Reduce the need for multiple applications when one application can take care of both Internet browsing as well as functioning as a package manager.  Clutter is reduced as well.  

6.  To possibly support Ubuntu's progress, ads can be placed next to search results.  Please do not be selfish: you've gotten an operating system entirely for free, you pay absolutely nothing; the least you can do is view several text-based ads that could help Ubuntu.  Again, don't be selfish.  No one likes ads, but this is for a good cause.  This is JUST AN IDEA.  

You all can add more ideas, and I am sure there are cons, but I am just throwing around ideas.  I already know Conary is browser-based, but Ubuntu does not use Conary.

> **ahaslam said:**
> Have you tried Foresight Linux?
[http://www.foresightlinux.org/screenshots/view/fsm/](http://www.foresightlinux.org/screenshots/view/fsm/)

here's a better look at the rPath package manager used by Foresight:
[http://www.flickr.com/photos/93809254@N00/sets/72157600336901509/show/](http://www.flickr.com/photos/93809254@N00/sets/72157600336901509/show/)


> **Henaro said:**
> Why don't we just all move to the terminal.  

1.  Eats up less RAM.
2.  Everyone has one.
3.  No messy GUIs.
4.  No matter which operating system you come from, the design is so familiar!  


;)

> **IYY said:**
> I don't even bother loading synaptic up. Seriously, is it that difficult to type

```
apt-cache search appname
sudo apt-get install appname
```

I honestly find it easier to use the terminal also.

---

### Post by zeller on 2007-12-05
I tried simply installing the cnr.com client from their website and it crashed my laptop midway through setup. Great idea, huh?

---

### Post by sageb1 on 2007-12-05
> **Henaro said:**
> Why don't we just all move to the terminal.  

1.  Eats up less RAM.
2.  Everyone has one.
3.  No messy GUIs.
4.  No matter which operating system you come from, the design is so familiar!  


;)

and an update-manager-like browser based on w3m.

---

### Post by sageb1 on 2007-12-05
> **S3Indiana said:**
> How does Google solve not knowing the package name in the first place???

just as apt-cache search can find out what package you might need without showing you which packages are installed, Google can do this too as long as you include the flavor of Linux you are using.

Yes, Synaptic knows what is installed and so does update-manager.

Though I have to add that it no longer seems safe to use a web browser to install new packages after having to GKSU into the specific update management app.

So the browser has to check to make sure a non-root user is using it to do upgrades and ensure that a gksu'd child of the browser is used instead.

Hm, this is sort of reminding me of Konqueror.

---

### Post by mdsmedia on 2007-12-05
> **RAV TUX said:**
> here's a better look at the rPath package manager used by Foresight:
[http://www.flickr.com/photos/93809254@N00/sets/72157600336901509/show/](http://www.flickr.com/photos/93809254@N00/sets/72157600336901509/show/)

I honestly find it easier to use the terminal also.

I think it's easier to use the CLI...IF you know exactly which package you want, AND you know the command to use.

I can use some of the basic commands, but if I don't know which package to install the CLI is not useful for this purpose. If I know exactly what I want to install I'll use the CLI. If I don't I'll use Synaptic.

I don't see the point of web-basing the package management. So it (arguably) uses less resources. Does this really matter if you're installing a package? I can see the cons though, like security of SU login.

EDIT: I just used apt-cache search for the first time...that's awesome :) and so much easier and quicker than Synaptic. You learn something every day :)

---

