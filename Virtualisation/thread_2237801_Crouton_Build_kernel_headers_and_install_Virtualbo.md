---
title: "Crouton Build kernel headers and install Virtualbox (x86)"
date: 2014-08-04
forum: Virtualisation
---

### Post by Domgoa on 2014-08-04
Greetings,

I am following these [instructions]("https://github.com/dnschneid/crouton/wiki/Build-kernel-headers-and-install-Virtualbox-(x86)") on how to build the header kernel for my Chromebook, I'm using Crouton to run Ubuntu 12.04 LTS.

But i do not completely understand how to proceed through a particular portion of the instructions.

I'm on the portion after i finished running the code below.

Code:

$ cd kernel
$ vi chromeos/config/base.config

And i have changed, [COLOR=#333333][FONT=Helvetica]CONFIG_ERROR_ON_WARNING=y to [/FONT][/COLOR][COLOR=#333333][FONT=Helvetica]CONFIG_ERROR_ON_WARNING=n

I do not know how to proceed afterwards through the terminal to enter the following codes below.

Code:
[/FONT][/COLOR]$ ./chromeos/scripts/prepareconfig chromeos-intel-pineview
$ make oldconfig[COLOR=#333333][FONT=Helvetica]

All assistance is welcomed.[/FONT][/COLOR]

---

### Post by Doug S on 2014-08-04
From your description, it is not clear to me what the problem is. You just type in (or copy and paste) those next two commands into your terminal session.
I assume you are doing that and it isn't working for some reason. Could you post more information as to error or warning messages displayed.

---

### Post by Domgoa on 2014-08-04
Its terminal related, i dont know all the terminal terminology so bear with me.

I do not known how to get [**(precise)elohim@localhost:~$** ] after i have edited ([COLOR=#333333][FONT=Helvetica]CONFIG_ERROR_ON_WARNING=y to [/FONT][/COLOR][COLOR=#333333][FONT=Helvetica]CONFIG_ERROR_ON_WARNING=n[/FONT][/COLOR]), how do i save this change within the terminal?

So i must know how to save my edit and how to get back **(precise)elohim@localhost:~$** so i may input the proceeding codes.

When i enter the codes in a new terminal window it dose not work.

Code:
$ ./chromeos/scripts/prepareconfig chromeos-intel-pineview
$ make oldconfig

---

### Post by Doug S on 2014-08-04
I don't use vi myself ( I use nano), but wouldn't you write out the modified file with ":w" and then exit vi with ":q". Look [here ]("http://www.cs.colostate.edu/helpdocs/vi.html")for some vi commands
Depending on the permissions of the config file you are editing, you might need to run vi under sudo.

---

