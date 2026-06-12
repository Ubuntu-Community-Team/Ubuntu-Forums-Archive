---
title: "[Arch] I just discoverd &quot;packer&quot; a much faster &amp; more efficient yaourt replacement:"
date: 2010-01-24
forum: The Cafe
---

### Post by handy on 2010-01-24
**bruenig**, has been working very fast since first making his *packer* available to the Arch community on the 5th Jan, the speed of development is amazing, with regard to bug fixes & feature requests.

I expect that packer could end up replacing yaourt as the community favoured pacman - AUR wrapper, as it is 14 times faster & it searches properly. i.e. it has shown how bad yaourt's search results are, as well as the fact that there is a lot of very poor code in yaourt.

I have been happy using yaourt since I started with Arch, but I certainly have to wait for it to varying degrees, every time I use it.

All in all packer is very good news for Arch users.

[http://bbs.archlinux.org/viewtopic.php?id=88115&p=1](http://bbs.archlinux.org/viewtopic.php?id=88115&p=1)

---

### Post by ~sHyLoCk~ on 2010-01-24
+1 for packer. Even though I prefer to manually upgrade packages from AUR and I use pacman-color for official packages, I find packer pretty neat for dealing with AUR packages.

---

### Post by n0dix on 2010-01-25
It's curious that a heard of packer program from a ubuntu forum and not for Arch one. 

Btw, the packer it's really awesome. This kind of things do the Arch community very pleased. ;)

---

### Post by handy on 2010-01-25
The developer of packer is blowing everyone away with his focus!  He has been called a coding machine. :)

Someone will point out a bug, or ask for a valid feature to be incorporated & in no time flat *bruenig* posts to do a packer -S packer, to get the new changes.

If *bruenig* maintains this kind of commitment to packer, it should gain a great reputation fast.

It is winning converts from yaourt very quickly as it is.

I agree, yaourt hasn't let me down either, but I do have to wait for it, & from tests shown on the packer thread, yaourt misses a lot in searches, which is the kind of problem you have, when you don't think you have a problem...

Here is one persons simple speed test results:


[I]yaourt -Ss firefox
real 0m8.516s
user 0m4.516s
sys 0m3.150s

packer -Ss firefox
real 0m0.735s
user 0m0.313s
sys 0m0.220s [/I]

From the thread by *bruenig*:

[I]The proper way to do this is grep $file. I have seen some very new bash coders use cat file | grep, but I have never seen someone use something as astonishingly redundant and slow as echo $(cat $file) | grep.

There are dozens of other examples like this. But the real issue is the performance such shoddy coding creates.

The command yaourt -Ss python takes 56.280 seconds to execute.

The command packer -Ss python takes 4.146 seconds to execute.

Yaourt is 13.5 times slower than packer. That is pretty serious.

Other examples abound, but that gives you a sense. Yaourt is just sloooooow.[/I]

&&

*Another thing you might want to realize is that yaourt search literally does not work. As in, it does not find all of the matches it should. Try 'yaourt pacman wrapper' and then 'packer pacman wrapper' to see. Yaourt is not finding over half of the aur packages it should be. In addition to this, yaourt -Ss pacman wrapper does not even work! It seems to search for all things that match 'pacman' OR 'wrapper'! What in the hell is that.*

---

### Post by n0dix on 2010-01-25
Hey Handy, you get a several benchmarks, ;) you really love this package.

One question: the argument -Scc doesn't work with packer? I forget if a try it :(.

---

### Post by Xbehave on 2010-01-25
```
time apt-cache search firefox
<snip>
real    0m0.704s
user    0m0.509s
sys     0m0.042s
```
do i win something? :P

But seriously your benchmark seams unfair as after youaurt has been run many of the index files will be in ram so packer will need to read less data of the disk.

---

### Post by n0dix on 2010-01-25
> **Xbehave said:**
> ```
time apt-cache search firefox
<snip>
real    0m0.704s
user    0m0.509s
sys     0m0.042s
```
do i win something? :P

But seriously your benchmark seams unfair as after youaurt has been run many of the index files will be in ram so packer will need to read less data of the disk.

Yes, it is, but how can you flush the memory ram?

---

### Post by handy on 2010-01-25
> **Xbehave said:**
> ```
time apt-cache search firefox
<snip>
real    0m0.704s
user    0m0.509s
sys     0m0.042s
```
do i win something? :P

But seriously your benchmark seams unfair as after youaurt has been run many of the index files will be in ram so packer will need to read less data of the disk.

I didn't do the test, so I can't tell you how the tester set it up.

What I do know, is that packer in my experience, without a stop watch or testing in any other way, is MUCH faster than when I use yaourt.

Which is why I'm enthusiastic.  

The benchmarks & the fact that yaourt misses things in certain kinds of searching (at least) don't matter to me.  The obviously speedy experience, plus the fact that the creator is very serious about making packer the best it can be has one me over.

Good stuff all-round. :)

---

### Post by Xbehave on 2010-01-25
> **n0dix said:**
> Yes, it is, but how can you flush the memory ram?
Use up all your ram and the caches will be plushed to disk, It's not worth the effort but you should run each one atleast twice (and take the second result).

p.s from what you've said packer sounds much better, i'm just a benchmark nazi.

---

### Post by dragos240 on 2010-01-25
I still have an arch box at my house, I will test it.

---

### Post by handy on 2010-01-25
> **n0dix said:**
> Hey Handy, you get a several benchmarks, ;) you really love this package.

One question: the argument -Scc doesn't work with packer? I forget if a try it :(.

When you want to use -Scc, you use pacman.

packer isn't a pacman replacement, it is a yaourt replacement, that transfers some pacman commands directly to pacman, due to user requests.

[I]```
handy ~  $  packer --help
usage: packer [option] [package] [package] [...]

    -S          - installs package
    -Syu|-Su    - updates all packages
    -Ss         - searches for package
    -Si         - outputs info for package
    -G          - download and extract aur tarball only

    --ignore    - takes a comma-separated list of packages to ignore
    --noconfirm - do not prompt for confirmation
    --auronly   - only do actions for aur
    --devel     - update devel packages during -Su
    --skipinteg - when using makepkg, do not check md5s
    -h          - outputs this message
 
```[/I]

---

### Post by n0dix on 2010-01-25
> **handy said:**
> When you want to use -Scc, you use pacman.

packer isn't a pacman replacement, it is a yaourt replacement, that transfers some pacman commands directly to pacman, due to user requests.

[I]```
handy ~  $  packer --help
usage: packer [option] [package] [package] [...]

    -S          - installs package
    -Syu|-Su    - updates all packages
    -Ss         - searches for package
    -Si         - outputs info for package
    -G          - download and extract aur tarball only

    --ignore    - takes a comma-separated list of packages to ignore
    --noconfirm - do not prompt for confirmation
    --auronly   - only do actions for aur
    --devel     - update devel packages during -Su
    --skipinteg - when using makepkg, do not check md5s
    -h          - outputs this message
 
```[/I]

Thanks a lot for the aclaration.=D> I probed packer and it is really awesome, eventually replace yaourt.  :guitar:

---

### Post by handy on 2010-01-25
**@n0dix:** As far as the use of *-Scc* goes, I really don't think it is a good idea.

If you ever need to downgrade any packages to get out of trouble, & you don't have the packages in your */var/cache/pacman/pkg/* then you have just made what would have been a really quick & simple fix to be a lot more difficult & time consuming.  

Especially if the problem you have has destroyed your ability to connect to the internet.  

You then have to use a LiveCD or another computer to go & find redundant packages, install them back in the cache/ & then do the *pacman -U <path.to.package/package.name.pkg.tar.gz>* to install the package.

I think that after we are happy with the quality of an *-Syu --aur* (by whatever means) that doing a *pacman -Sc* is the best idea, as it removes all but the packages we have installed from our cache.  

So if/when we upgrade into trouble, we can look at the pacman.log & the .../cache/pacman/pkg/ & just copy & paste the names of the packages that we need to downgrade, which after you have the experience you find is really quick & easy.

Using the *-Sc* method means that at worst we have 2 sets of packages in our cache, before we clean it with *-Sc*, after which we only have one. :)

I wrote a bit of a how-to on this subject over here it is a bit clearer than what I have written here ;):

[http://www.ostalk.org/showthread.php?tid=78](http://www.ostalk.org/showthread.php?tid=78)

There are some other useful Arch how-to files in that sub-forum also.

---

### Post by n0dix on 2010-01-25
> **handy said:**
> **@n0dix:** As far as the use of *-Scc* goes, I really don't think it is a good idea.

If you ever need to downgrade any packages to get out of trouble, & you don't have the packages in your */var/cache/pacman/pkg/* then you have just made what would have been a really quick & simple fix to be a lot more difficult & time consuming.  

Especially if the problem you have has destroyed your ability to connect to the internet.  

You then have to use a LiveCD or another computer to go & find redundant packages, install them back in the cache/ & then do the *pacman -U <path.to.package/package.name.pkg.tar.gz>* to install the package.

I think that after we are happy with the quality of an *-Syu --aur* (by whatever means) that doing a *pacman -Sc* is the best idea, as it removes all but the packages we have installed from our cache.  

So if/when we upgrade into trouble, we can look at the pacman.log & the .../cache/pacman/pkg/ & just copy & paste the names of the packages that we need to downgrade, which after you have the experience you find is really quick & easy.

Using the *-Sc* method means that at worst we have 2 sets of packages in our cache, before we clean it with *-Sc*, after which we only have one. :)

I wrote a bit of a how-to on this subject over here it is a bit clearer than what I have written here ;):

[http://www.ostalk.org/showthread.php?tid=78](http://www.ostalk.org/showthread.php?tid=78)

There are some other useful Arch how-to files in that sub-forum also.

You are a master ;) this mini guide is very useful. 

I had not the need to do a downgrade, but i see the problem if i get one. I will follow your recommendation, use -Sc instead -Scc. 
Master, thanks for the mini guide again.

p.s: seems you had have a problem related to this. This guide is very detailed.

---

### Post by ~sHyLoCk~ on 2010-01-25
I think before -Sc you should have:
```
CleanMethod = KeepInstalled

```
Oh and put :
```
ILoveCandy
``` for lulz :P

---

### Post by handy on 2010-01-26
> **n0dix said:**
> 
You are a master ;) this mini guide is very useful. 

I had not the need to do a downgrade, but i see the problem if i get one. I will follow your recommendation, use -Sc instead -Scc. 
Master, thanks for the mini guide again. 

Please don't call me master, the way it works is that the more you know, the more you know that you don't know... lol

> **n0dix said:**
> 
p.s: seems you had have a problem related to this. This guide is very detailed.

Yes I did have a problem, which is when I had to learn about downgrading.  So writing a how-to serves the dual purpose of helping someone else to hopefully avoid making life harder for themselves, & refreshing my memory in the future if I forget how to do it.  Which is quite useful as my memory ain't what it used to be... ;)

---

### Post by Dj Melik on 2010-01-26
Xyne's bauerbill is awesome too.

---

### Post by handy on 2010-01-26
> **Dj Melik said:**
> Xyne's bauerbill is awesome too.

So I've heard.

I tried powerpill in the past, but it made no difference to my download speeds, as I get full speed anyway.

It's cool that there are a variety of yaourt replacements in existence. :)

---

