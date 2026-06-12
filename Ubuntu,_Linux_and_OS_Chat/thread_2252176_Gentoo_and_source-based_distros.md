---
title: "Gentoo and source-based distros?"
date: 2014-11-09
forum: Ubuntu, Linux and OS Chat
---

### Post by SagaciousKJB on 2014-11-09
Well i was reading up a little bit about Gentoo the other night, never really knew what it was all about before.  Anyway, aside from the whole "You choose everything!" principle, what I thought seemed cool was that when you isntalled software from the responsitories with their package management system, that it installed it as source with custom optimization options.  The idea is that it will make software tailor-suited to your hardware which sounds really cool.

So my quesiton is kind of two pronged..  First of all, does compilinng software system-wide like this really add a performance increase over a binary based system?  Like, compare Arch to Gentoo for example...  If you started compiling everything on Arch, would it get any performance increase, or still be held back by the bianries that the system is based on?

I downloaded a LiveCD of "Sabayon" which is I guess an out-of-the-box type distro, trying to get all the most common power user stuff to work right off.  But it's based on Gentoo and has both a binary package management system and the source management system.  I want to try it but I'm already out of partioning space on my drive, and if I used a VirtualMachine it wouldn't have the hardware optimization so I doubt I'd see any performance increase--likewise running from a LIveCD I'm not sure would be a good comparison either.

Anyway I know that I can build packages from source using apt, couldn't I just build a few choice software packages my self with opitmization flags and expect a performance increase on Ubuntu?  If a part source/part binary distro like Sabayon would offer any performance icnrease, it should work on a Debian base (mostly binaries?) too right?

---

### Post by tgalati4 on 2014-11-10
It's a good learning experience.  I have read that the performance improvement is 2%.  If it was much greater, then you would see more source-built distros out there.

Any binary distro will also have a source repository that you can download any package and build just that package.  That is helpful if you want to tweak a specific package, use add-ons, or just play around to see how a specific package works.

Most of the packages have standard optimization flags used during compilation time.  You can prove this to yourself by timing how long it takes to perform lengthy operations in GIMP or Audacity or other CPU-intensive packages.  Test the binary version and the source-built version and they will be the same.  If they are not, then you would hear about it.

Now, if you are doing scientific computing with your own code, you can get significant improvements with different levels of optimzation (-O1, -O2, -O3, etc) and that you can test.  With the normal packages that come with a linux distro, most are optimized as much as possible already.  Pick a couple of standard packages and test them yourself and report your results in this thread.

You can't mix and match binaries between distros because the dependent libraries are grouped differently in each distro.  So, although it may be possible to run Sabayon binary in Ubuntu, if there are any dependency differences, you will encounter breakage.

---

### Post by buzzingrobot on 2014-11-10
IMO, source-based distros like Gentoo should be used if it's the actual process of crafting and building your system that you are after, rather than simply using it.

Contemporary hardware is more than adequate for desktop Linux. I've seen reports that the typical speed boost from building an entire Gentoo desktop with full compiler optimizations versus building the same desktop without the optimizations is something less than 10 percent.  For me, that's not worth it.  A little money adding RAM or a better video card is more likely to noticeably boost performance.

As you said, it isn't that difficult to rebuild a source package, which you might try if a specific piece of software was recalcitrant. 

Weeding out unwanted software during the install is fine, but all that does is avoid using a bit of drive space.

I'm not trying to talk you out of it.  But I wouldn't expect a big payoff.

---

### Post by mips on 2014-11-10
> **SagaciousKJB said:**
> 

So my quesiton is kind of two pronged..  First of all, does compilinng software system-wide like this really add a performance increase over a binary based system?  Like, compare Arch to Gentoo for example...  If you started compiling everything on Arch, would it get any performance increase, or still be held back by the bianries that the system is based on?

With todays hardware I'm gonna say it's not really worth it and you probably would not notice any difference between running say optimised Gentoo compiled code vs say Arch. I also don't have the patience to compile everything from scratch when I can simply install a binary. I had this idea to install Gentoo a while ago but that idea faded very quickly when the beer induced nostalgia faded away :biggrin:

---

