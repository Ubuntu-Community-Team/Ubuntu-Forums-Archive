---
title: "Lubuntu 12.04 and LTS"
date: 2013-06-11
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain2012 on 2013-06-11
My understanding is that Lubuntu 12.04 is not a LTS even though Ubuntu 12.04 is. But since Lubuntu uses the same repositories as Ubuntu does it mean that it will still get security updates for 5 years? So what is the difference? If it is just the lxde stuffs not getting updates then it doesn't sound like an OS upgrade is necessary when 13.10 comes out.

I ask because I have installed lubuntu 12.04 on someone's old netbook and the question of upgrade has come up. I know that 12.10 doesn't work on it.

---

### Post by sudodus on 2013-06-12
You are right, Lubuntu 12.04 has no LTS.

The LXDE stuff, but also the application software, that is unique to Lubuntu (and not included in any of the LTS versions) will not be maintained officially.

The risk may not be big, but it will be increased, that one of those packages will get known security issues, and the end user will not get any update. So my policy is to say "If you want to use it, OK. but you are on your own." I would not recommend it to someone else (for example here in the Ubuntu Forums).

I would recommend to upgrade to a new Lubuntu version or change [desktop environment] to Xubuntu, which has LTS until April 2015.

'Only the window manager Openbox' is a minimalistic alternative. I think it has LTS because it is part of Kubuntu (a light KDE alternative) which has LTS. This might work if the computer is too weak to run Xubuntu, and some important driver for the particular computer was dropped in Lubuntu 12.10 or 13.04.

But you can also select [LXLE]("http://www.lxle.net/"), a respin of Lubuntu, which promises to keep its packages up to date during the whole LTS period of Ubuntu 12.04.

---

