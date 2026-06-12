---
title: "Suggestion: investment in minimal/server installs, especially as far as WiFi"
date: 2016-12-19
forum: Ubuntu, Linux and OS Chat
---

### Post by lopmenhed on 2016-12-19
There's a lot of interest in the Linux world in minimal installations. There are a number of distributions aimed specifically at this need, from aggressive ones like Tiny Core Linux to those that simply don't install many packages by default like BunsenLabs or the one such major Ubuntu derivative I know of, Bodhi Linux (I'm not counting the Ubuntu Mini Remix because it's intended as a base for further development and, among other things, has no installer of its own).

Here I'm carefully using the term "minimal" as distinct from "lightweight." Lubuntu doesn't need a lot of RAM or a fast processor (so I believe it's correct to call it "lightweight"), but it does install a lot of stuff (so it's not "minimal").

A purer approach than using BunsenLabs or Bodhi is to take one of the cornerstone distributions like Debian, Ubuntu, or Arch, install the base system, and go from there. I recently did this with Ubuntu and felt like I was going well outside of what was well-supported by the tools. So I came here to give the feedback that I wish this was a more supported operation. As I said above, my perception is that there's a lot of interest in minimal installs. As for the struggles I had installing, the piece that generalizes is this: the wireless support is limited. The mini ISO only has limited wireless modules, and what's more [doesn't support UEFI]("https://help.ubuntu.com/community/Installation/MinimalCD"), but fair enough, it's a *mini* ISO. So I switched to the server ISO. I was surprised to find that the server ISO *also* didn't support my wireless card, so I had to sneak the relevant modules in. This is a real ninja process, starting with just figuring out what the modules are in the first place and where to get them. If there hadn't been [a question on askubuntu]("http://askubuntu.com/questions/792459/thinkpad-t450s-wireless-interface-not-detected-when-installing-ubuntu-16-04-mini/817157#817157") that was similar enough to show up in a search, I would have been dead meat. I guess the assumption is that if you're setting up a server, you might have wired internet. But if server installs are the *de facto* way to do minimal installs, and if more and more computers are being sold without ethernet jacks, that's no longer a safe assumption. So in conclusion I think it would be great if future versions of Ubuntu made it easier for those of us who would struggle to add modules to our install media to pull of minimal installs, whether using the server ISOs or otherwise.

---

### Post by nothingspecial on 2016-12-19
> **lopmenhed said:**
>  I guess the assumption is that if you're setting up a server, you might have wired internet.

I guess your guess is correct. Why would you have a sever with wifi only?

ubuntu-server is aimed at servers. {U,L,X,K}u*buntu is aimed at personal computers with ease of installation and use in mind. If you want to mess about with base installs and such, go ahead, but Ubuntu is not designed for this.

---

### Post by tea for one on 2016-12-19
> **lopmenhed said:**
> There's a lot of interest in the Linux world in minimal installations

Have a quick look at this project:-

[https://unit193.net/xubuntu/](https://unit193.net/xubuntu/)

I have installed it on a 32GB HP Stream Notebook and added a few applications.

I'm happy with it so far.

Of course, it also works as a live CD/USB so you can test it as long as you wish.

Kind regards

---

### Post by lopmenhed on 2016-12-20
> **nothingspecial said:**
> I guess your guess is correct. Why would you have a sever with wifi only?

ubuntu-server is aimed at servers. {U,L,X,K}u*buntu is aimed at personal computers with ease of installation and use in mind. If you want to mess about with base installs and such, go ahead, but Ubuntu is not designed for this.
From what I could tell this forum what the right place to give a +1 for base installs and such, to the extent there is such a place. Making the set of WiFi modules on the server install ISO match regular Ubuntu seems to me (a person with *no*&#8203; relevant experience) like low-hanging fruit.

**[COLOR=#000000]@tea for one[/COLOR]**[COLOR=#000000], thank you for the pointer to Xubuntu Core. I have not tried it (was going for something lighter than Xubuntu), but if it's based on the Ubuntu Mini ISO it will have the same issues.[/COLOR]

---

### Post by speedwell68 on 2016-12-20
> **tea for one said:**
> Have a quick look at this project:-

[https://unit193.net/xubuntu/](https://unit193.net/xubuntu/)

I have installed it on a 32GB HP Stream Notebook and added a few applications.

I'm happy with it so far.

Of course, it also works as a live CD/USB so you can test it as long as you wish.

Kind regards

That is what I am using on  my media server and it works beautifully.  Install it and add just the extra software you need job done.

---

### Post by Habitual on 2016-12-20
[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

---

### Post by nothingspecial on 2016-12-20
> **lopmenhed said:**
> From what I could tell this forum what the right place to give a +1 for base installs and such, to the extent there is such a place. Making the set of WiFi modules on the server install ISO match regular Ubuntu seems to me (a person with *no*&#8203; relevant experience) like low-hanging fruit.

I don't think I put my last post very well :)

Ubuntu desktop edition and it's official flavours are designed to just work with little or no fuss, for people who have little care or knowledge of how the operating system works (or people who just want an easy life).
Ubuntu server is designed to work with no fuss on servers, for use by companies that need their stuff to work with as much efficiency as possible, have paid support from Canonical if they choose and, like I said, who would have a wifi only server? and why would Canonical support one? Why include something on a server that is unnecessary for the target market?  

Of course, this forum is a perfect place to come if you need help with a server install and you are struggling with wifi, however I doubt Canonical is going to change what they include in their server isos because some people might want to build up to a desktop. It's not what they are about or what they design their products for.

---

### Post by lopmenhed on 2016-12-29
> **nothingspecial said:**
> 
Of course, this forum is a perfect place to come if you need help with a server install and you are struggling with wifi, however I doubt Canonical is going to change what they include in their server isos because some people might want to build up to a desktop. It's not what they are about or what they design their products for.

In case someone eventually comes along with similar questions to my own: after some more looking I learned that there are some non-official lightweight Ubuntu derivatives based on Ubuntu/Lubuntu that have a more minimal philosophy including Bodhi Linux and Peppermint OS. Interestingly both of these also appear to have heavily modded desktop environments, but nonetheless they might have suited my original purposes fine. And of courses there are non-Ubuntu options such as BunsenLabs for anyone who wants to strike out that far from the subject of these forums.

---

### Post by kevdog on 2016-12-29
You want a base install with wifi modules --> Arch!!! That's the first thing that came to mind.  By default the base install doesn't come with the x-windows system, but it does allow for wireless setup.  After the base install you get to pick the packages you want to install -- that's how it works. It also teaches you how to boot strap a system with chroot -- a process similar if you've ever used jails.  I like Ubuntu a lot and use it daily, however it's not good for every purpose.

---

