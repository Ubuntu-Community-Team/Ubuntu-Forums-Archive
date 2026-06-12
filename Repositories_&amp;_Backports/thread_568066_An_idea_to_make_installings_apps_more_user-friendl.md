---
title: "An idea to make installings apps more user-friendly:"
date: 2007-10-05
forum: Repositories &amp; Backports
---

### Post by DaveTheAve on 2007-10-05
```
<a href='repo://archive.ubuntu.com/ubuntu/repo'><img src='images/addRepos.jpg' /></a>
```

Just an Idea and I’ll know I’ll get flamed for it but remember, I’m a full-time linux user and have no problem manually adding repos, but I’m thinking more for the new Dell/linux users.

Why can’t we add a new protocol to our browsers that will allow people to just click a link or an image and run the script, repo://archive.ubuntu.com/ubuntu/repo in the above example. Before the script is even ran; however, we MUST inform the user that the site is trying to change the apt/source.list file and inform them that such action is EXTEMELY dangerous on their porn sites they visit ever so frequently.

I doubt something like this will take effect but it’s an idea to help reach a more user-friendly installation/customization. I’d love it for linux as easy as Windows to install applications; we already have them beat for updating.

Now vent to me about how much this idea "sucks" and how linux should not be as easy to install apps as windows and how I should go hang myself.

---

### Post by Jussi Kukkonen on 2007-10-05
Maemo has something like this. A typical ".install" file looks like this:
```
[install]
catalogues = foobar
package = maemofoo

[foobar]
name = Foobar Catalogue
name[en_GB] = Foobar Catalogue
name[de_DE] = Foobar Katalog
uri = http://foobar.com/repository
components = main

```
Clicking that would add repository *foobar* if it's not in sources.list already and then proceed installing package *maemofoo* using apt. 

The problem with this is that software developers no longer have much incentive to make their software good enough for the official repos -- they can just tell people to add their own repository: "it's just one click!". As a result there are a gazillion repositories and no-one can keep track which ones are respectable (this is unfortunately the situtation with maemo). 
It's still a lot better than offering binary installer or .deb downloads.

---

### Post by DaveTheAve on 2007-10-05
Well, I feel Linux needs an easier way to install programs - if you're not a developer - and better hardware support. The latter of the two has already begain with [The Linux Driver Project]("http://www.linuxdriverproject.org/"); now we need to tackle the first.

I'm all for apt-get, aptitude, etc; however, sometimes you have to compile the program yourself - thats what we need to eradicate! To compile a program you need to make sure you have the *-dev or *-devel 's needed, than pray the ./configure will work, than pray the make will work. Once you'r done with all that praying you need to pray that the compiled application doesn't have anymore dependancys. (Though getlibs helps with that last part)

In short, we need an easier way to install non-ubuntu supported packages.

---

### Post by UbuWu on 2007-10-06
This will be included in Gutsy! In gutsy it will be possible to link from webpages to programs in the official repositories to install them. After some discussion, adding third party repositories and installing software from them was disabled for now.

If you are running Gutsy, you can try it out by clicking this link: [install Pychess now!]("apt:pychess")

---

### Post by DaveTheAve on 2007-10-06
Wow! But wait... that only install them IF the repo is already in apt/source.list.... but hey IT IS a step CLOSER!!!

---

### Post by pingpongboss on 2007-10-07
> **UbuWu said:**
> This will be included in Gutsy! In gutsy it will be possible to link from webpages to programs in the official repositories to install them. After some discussion, adding third party repositories and installing software from them was disabled for now.

If you are running Gutsy, you can try it out by clicking this link: [install Pychess now!]("apt:pychess")

haha wow holy cow, never knew it could do that.

---

