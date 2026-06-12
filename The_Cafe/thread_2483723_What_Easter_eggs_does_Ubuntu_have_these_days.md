---
title: "What Easter eggs does Ubuntu have these days?"
date: 2023-02-07
forum: The Cafe
---

### Post by Paddy Landau on 2023-02-07
We haven't seen this discussion for several years, and I wondered what the current status is?

Looking up Easter eggs for Linux, mostly it consists of terminal commands (usually that need to be installed) and weren't actually Easter eggs anyway, or a few defunct Easter eggs that no longer exist.

The only ones that I could find were Super Cow Powers, and GEGL Time in the mouse settings.

Any others?

I'm interested in 22.04 LTS, if that makes a difference, and I'd rather avoid having to install new programs, because that's not the point of an Easter egg.

[HR][/HR]
For those who don't know…

[SIZE=3]Super Cow Powers[/SIZE]

In a terminal, enter the command [FONT=courier new]apt[/FONT] (or [FONT=courier new]apt-get[/FONT]). The last line should read, "This APT has Super Cow Powers."
Enter the command [FONT=courier new]apt moo[/FONT] to get something that moos.

[SIZE=3]GEGL Time[/SIZE]

In Gnome (including Ubuntu 22.04), go to Settings > Mouse & Touchpad > Test Your Settings > click the button five times (left or right mouse button). The message "GEGL Time!" appears. If you scroll up, you'll see a certain animal (it disappears after about 4 seconds). I don't know what it's significance might be.

---

### Post by TheFu on 2023-02-07
```
$ banner Moo
#     #
##   ##   ####    ####
# # # #  #    #  #    #
#  #  #  #    #  #    #
#     #  #    #  #    #
#     #  #    #  #    #
#     #   ####    ####

```
I suspect that isn't what you seek?

You can play pong in emacs, sticking true to the well-known abbreviation that is e.m.a.c.s.
```

$ aptitude help
$ aptitude -v moo
$ aptitude -vv moo
$ aptitude -vvvvv moo
$ sudo can be set to 'insult mode', if you like. The sudoers manpage explains.

```L33T output from nmap option -oS
In firefox, enter about:mozilla into the URL field.

---

### Post by Paddy Landau on 2023-02-07
> **TheFu said:**
> ```
$ banner Moo
```
I suspect that isn't what you seek?
Correct. That's not an Easter egg, just an app that makes banners. It's not installed by default, anyway.
> **TheFu said:**
> You can play pong in emacs, sticking true to the well-known abbreviation that is e.m.a.c.s.
Hnn, that's interesting. I don't have emacs installed, so I installed it to try it, but I couldn't find Pong.
> **TheFu said:**
> ```
$ aptitude help
$ aptitude -v moo
$ aptitude -vv moo
$ aptitude -vvvvv moo
```
I don't have aptitude installed, but that one's good if you do.
> **TheFu said:**
> sudo can be set to 'insult mode'
Hmm, is that an Easter egg? I'm unsure :)
> **TheFu said:**
> L33T output from nmap option -oS
I'm sorry, I don't understand that :(

I installed nmap and ran:
```
nmap -oS L33T
```
but that just gave an error.
> **TheFu said:**
> In firefox, enter about:mozilla into the URL field.
Yes, that's a nice one :)

---

### Post by TheFu on 2023-02-07
> **Paddy Landau said:**
> Hnn, that's interesting. I don't have emacs installed, so I installed it to try it, but I couldn't find Pong.

It's hidden.  You have to know how to run it!  ;)
> **Paddy Landau said:**
> 
I don't have aptitude installed, but that one's good if you do.

aptitude is one of those "must have" tools for package management issues.  It can do things that no other tool can do.  Mainly, I like the way it will show alternative solutions to dependency issues and allow the admin to pick the one they want.  Sometimes I've had to look through 10 options before finding one that wouldn't do more harm than good.

> **Paddy Landau said:**
> 
Hmm, is that an Easter egg? I'm unsure :)

It makes sudo mistakes a little more snarky. If that isn't expected, it can be fun.

> **Paddy Landau said:**
> 
I'm sorry, I don't understand that :(
I installed nmap and ran:
```
nmap -oS L33T
```
but that just gave an error.

Try this: 
```
sudo nmap -oS - 192.168.1.1
```
Assuming your router is at that IP.  You can point at other machines or subnets, of course.

---

### Post by Paddy Landau on 2023-02-07
> **TheFu said:**
> It's hidden.  You have to know how to run it!  ;)
Hmm… Google needed!
> **TheFu said:**
> ```
sudo nmap -oS - 192.168.1.1
```
Well, that was unexpected, ha ha!

---

### Post by TheFu on 2023-02-07
There are a bunch of Star Wars related things too.  Some have died like the traceroute one, but many others exist.

---

