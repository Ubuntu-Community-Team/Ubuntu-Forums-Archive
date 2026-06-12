---
title: "The Endorsed-By-Linux project needs your help!"
date: 2007-02-11
forum: The Cafe
---

### Post by Adamant1988 on 2007-02-11
>  The problem:

Linux currently suffers from a confusing situation concerning hardware for the end-user. There is no well-kept list or any kind of branding to let users know if something will, or will not, work with their Linux distribution. Users have no way of knowing if a new printer will work for their distribution of Linux, if there will be major issues with their video card when they try to install that distribution, and more importantly they don't know what the fixes are for any problems that arise concerning hardware. There is no centralized point where users can find and shop for hardware that "just works" with Linux. There are currently hours of research involved in preparing to install Linux, or buy a new piece of hardware. We think that is unnecessary.

Our Goal:

Our goal is to offer a centralized point where people can find hardware that is recommended for their Linux distribution. Thus easing the research necessary to shop for new hardware. However, the list will also contain information needed to determine if the user's hardware will function when he or she switches to Linux, or change distributions even, and will give the user an idea of the work involved in that switch.
--------------------------------------------------------------------------------------------------------------------------

As you can tell, this is a daunting task, and we need all of the help we can get. We would like people from all walks of Linux to help us in this project. Anything at all would be useful, even just support!

We do need some skilled people to assist us though. Currently our needs include (but are not limited to) the following:
[list]
   [*] **Programmers**.
      We have decided that the best way to go about collecting the information about the specific hardware would be to write a client that is distro agnostic and would allow us to get detailed information on the hardware, while allowing the user to fill us in on things that a script can't tell us. (the current plan is to use python for the script, but that could be subject to change)

    [*] **Linux Experts**
      Obviously we need to know what information is relevant to collect when it comes to compatibility for hardware. Experts who know Linux inside and out would be of paramount important in helping us to figure out what information to collect, and what to leave out.

    [*] **Web designers**
      We currently have 1 web designer working with us, and I'm trying to assist in the design. However the more input and collaboration we have on the actual design for the site the better.
    [*] **Web Programmers**
      We have one we programmer working with us, but we won't turn away any help. The site is going to be fairly complex in design, and will require a lot of work to build, so having more help will surely be a good thing.
    [*] **Marketers**
      I myself have some training in this area, but any help is welcome.[/list]

We want to try to make Linux a more friendly place for everyone, by making it easier to find hardware for your computer, and sort out compatibility issues before they become relevant we make it easier for people to switch to Linux; Which we can all agree is a good thing. Thank you for taking the time to read this, please contact us if you have any questions.

Our current temporary forums are located at
[Endorsed By Linux](http://www.punbb-hosting.com/forums/endorsedbylinux/index.php)


- Adam.

-----------------------------------------------------------------------------------------------------
Q&A

**Question:**> Sounds like a great project. How is it going to work then will it be categorized by distro release kernel etc. Then list hardware compatible with it?

**Answer:**
The current plan is to categorize by each distribution release. We feel that needs to be done as sometimes there are great variations between two versions of an operating system in terms of hardware compatibility. So for instance, if you were to be looking for recommended hardware for Ubuntu you would be able to sort by individual releases

An example of how the menu hierarchy would work is:

>  Distribution:
-OpenSuse>
-- Suse 10.1
-- OpenSuse10.2

-Ubuntu>
--Dapper Drake 6.06
--Edgy Eft 6.10

When you select each name, you would then be brought to the page for that distribution, where you would select if you were looking for a Printer, Camera, etc. that would work with the system. That is how the RECOMMENDED hardware list would function.


If you merely wanted to check the compatibility of a piece of hardware you would do the reverse. You would see a hierarchal menu like this:

>  Select your hardware:

-Printer
-- HP
--- Deskjet
---- HP Deskjet All-in-One F335
-Scanner
-Digital Camera

You would then be directed to the page for this specific piece of hardware. Which would give you a selection of distributions that it has been used on, and how many times it's been found. There would be a "rating" (perhaps using the 5-star metaphor) for each distribution that it's been tested on. You would then select your distribution and see potential problem areas, what drivers to use, and so forth.

**Question:** > Sounds good. How will things be added, by those who visit the site? Will we have to login to submit? When do you all expect to be up in beta stage.

**Answer:** The current plan is to use a client to detect the hardware that is connected to the computer when the client scans. We are currently looking at different ways to make this client distro agnostic as there are already clients that exist but are distribution specific.
Some options we're considering are a firefox plugin/extension, or a python based client.

The client would be able to detect and gather much more information much quicker and more accurately than a user would be able to do themselves. The client will then ask for them to "fill in the blanks" if you will about the hardware, so we'll have both accurate information and the log of each individual users experience with that hardware. There will probably be a kind of check list for varying criteria (Worked "out of the box", etc.) So in terms of actually submitting data, there would be no required login, you would only need to use the client.

We're still working out the kinks the ideas and collecting all of the help we can get. Hopefully within the next week to two weeks we should be able to produce some kind of a road map. No beta is scheduled yet, however.

---

### Post by %hMa@?b&lt;C on 2007-02-11
How about a offical form, with a drop down menu to choose the hardware just up on the page so that emails can get us started off.  I would not mind reserving [email]endorsedbylinux@gmail.com[/email]
If you want, I can whip that up, just give the word, also what should be given.
also please list the team members, so we can organize a little better.  I am excited about this project.

---

### Post by nalmeth on 2007-02-11
> **Answer:** The current plan is to use a client to detect the hardware that is connected to the computer when the client scans. We are currently looking at different ways to make this client distro agnostic as there are already clients that exist but are distribution specific.
Some options we're considering are a firefox plugin/extension, or a python based client.

The client would be able to detect and gather much more information much quicker and more accurately than a user would be able to do themselves. The client will then ask for them to "fill in the blanks" if you will about the hardware, so we'll have both accurate information and the log of each individual users experience with that hardware. There will probably be a kind of check list for varying criteria (Worked "out of the box", etc.) So in terms of actually submitting data, there would be no required login, you would only need to use the client.

We're still working out the kinks the ideas and collecting all of the help we can get. Hopefully within the next week to two weeks we should be able to produce some kind of a road map. No beta is scheduled yet, however.
Isn't this exactly what Do-Hickey is doing? 
Are you going to use their client for Endorsed-by-linux?

Might save a lot of work if you guys worked together :KS

---

### Post by Adamant1988 on 2007-02-11
> **nalmeth said:**
> Isn't this exactly what Do-Hickey is doing? 
Are you going to use their client for Endorsed-by-linux?

Might save a lot of work if you guys worked together :KS

We'll definitely talk with them if it will save us some time.  We would like to be able to start quickly, but we don't want to rush.  We'll talk to them.

---

### Post by %hMa@?b&lt;C on 2007-02-11
> **nalmeth said:**
> Isn't this exactly what Do-Hickey is doing? 
Are you going to use their client for Endorsed-by-linux?

Might save a lot of work if you guys worked together :KS
great idea, I completely forgot about the dohickey project! Does it actually work now, as I remember it did just print the name of each piece of hardware without listing if it works.
I did register [email]endorsedbylinux@gmail.com[/email]

---

### Post by poohbear1616 on 2007-02-11
Something I would like to see is a list by brand and model #s for new factory built systems that could be posted to about different distros that were tried and if it is known to work or didn't work at all or if a specific piece of hardware would not work.

That way if someone found a system on the net or at there local place they could write down the brand and model and see what distros have been tried and will work without having to know specific hardware details of whats inside the box.

Here's my example:
I bought a new compaq model #sr2163wm three days ago. Then I could look up or post what I've tried such as (actual results): 
Ubuntu Dapper: No sound but works well other wise.
Fedroa Core 6: Doesn't work at all. Will not boot or install
Dream Linux 2.2: Everything works very well.
And so on.

Now your idea is great. I have an old system that I built myself that your idea would prove very useful for.

---

### Post by %hMa@?b&lt;C on 2007-02-11
whoops, double post

---

### Post by Adamant1988 on 2007-02-11
> **poohbear1616 said:**
> Something I would like to see is a list by brand and model #s for new factory built systems that could be posted to about different distros that were tried and if it is known to work or didn't work at all or if a specific piece of hardware would not work.

That way if someone found a system on the net or at there local place they could write down the brand and model and see what distros have been tried and will work without having to know specific hardware details of whats inside the box.

Here's my example:
I bought a new compaq model #sr2163wm three days ago. Then I could look up or post what I've tried such as (actual results): 
Ubuntu Dapper: No sound but works well other wise.
Fedroa Core 6: Doesn't work at all. Will not boot or install
Dream Linux 2.2: Everything works very well.
And so on.

Now your idea is great. I have an old system that I built myself that your idea would prove very useful for.


Please by all means, feel free to raise that concern on our forums! any input would be great!

---

### Post by macogw on 2007-02-11
well for lappies there's always linux-on-laptops.com and tuxmobil.org

---

### Post by Adamant1988 on 2007-02-11
> **macogw said:**
> well for lappies there's always linux-on-laptops.com and tuxmobil.org

We're currently discussing a way to include complete systems.

---

### Post by %hMa@?b&lt;C on 2007-02-12
We are currently working on the for the hardware scanner.  Any help on any facet of the project would be greatly appreciated.

---

### Post by Adamant1988 on 2007-02-12
Any comments or suggestions on our forum would be greatly appreciated (we're trying to get them all in one place so we can sort them).  Thank you all for the support and the input!

---

### Post by DoctorMO on 2007-03-12
Peek a boo, hello I can't help noticing that your project is quite similar to my own; do let me know how things get on and if your going to do a client scanner let me know what solution you manage for some of the problems as we might be able to fix each others flaws.

Good luck: [http://www.dohickey-project.com](http://www.dohickey-project.com)

---

### Post by ssam on 2007-03-12
good idea, but i think you might need to change the name.
Linux is a trade mark, and linus might not want people implying that he endorses something.

you should check with [http://www.linuxmark.org/](http://www.linuxmark.org/)

otherwise, good luck with the project

---

