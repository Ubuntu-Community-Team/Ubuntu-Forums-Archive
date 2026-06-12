---
title: "vboxlinuxadditions guest"
date: 2023-08-18
forum: Virtualisation
---

### Post by cris455 on 2023-08-18
Hi,

Want to add guest additions on server, went to deviced -> upgrade guest additions. 
Ran up to 60% and then gave an error:
Running update file "/bin/sh" on guest failed: VERR_INTERNAL_ERROR_5.

What is internal error 5? Has anyone had this problem before? Did you solve it?

---

### Post by TheFu on 2023-08-18
So, this question belongs in the "Virtualization" sub-forum.

Did you install the build-essential package and other dependencies first?  
Whenever there are errors like this, take the error, put it into a search engine, there will likely be 50+ results.
I put :
> vbox Running update file "/bin/sh" on guest failed: VERR_INTERNAL_ERROR_5.
into a search and was provided many solutions.  Did you try those? Which ones?

One of the solutions seems to be tied to Vagrant. Are you using vagrant?  If so, mention that too.

> What is internal error 5? Has anyone had this problem before? Did you solve it? 
That's why web search engines are really good.

The virtualbox manual is really very good, BTW.  [https://www.virtualbox.org/manual/](https://www.virtualbox.org/manual/)  Not that is has anything to do with this.  It is just handy to know it is there.  I like chapter 6 - networking.   [https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html) is all about installing the *Guest Additions*.

And one last group of things.  We cannot read your mind. We need to be told
[LIST]
[*]Which OS?  If it isn't some Ubuntu/linux, we need to know that.
[*]Which OS release?  **lsb_release -d** will tell us the debian-based release information.
[*]Which Virtualbox version? At the high level, there's a GNU version and an Oracle version. They have important differences.
[*]What you've tried already to fix this.
[*]Any setup/dependencies already installed?
[*]Did it work previously? Say it worked on this machine with this OS the last 2 yrs, if that is so.  If it is a brand new install, tell us that too.
[*]How new are you to what you are trying to accomplish?  Everyone makes mistakes. Some dumb, some extremely subtle. We all do it.
[/LIST]
Saying "latest release" doesn't mean anything. We don't know what you think is the latest.  Be specific. Use numbers.

You wrote:
> Ran up to 60%
I have no idea what that actually means?  Is there a progress bar?  Was there RAM being used? CPU?  Something else?  Please provide details. Don't make us guess.

Then when someone asks for more information, provide it. Use the commands provided. If multiple things are requested, provide them all if they don't clearly say this OR that OR the other.  

Asking questions and providing solid information will get better answers.  Sometimes, gathering the information will lead to a solution. Happens to me all the time.

---

### Post by ajgreeny on 2023-08-18
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

### Post by MAFoElffen on 2023-08-19
@TheFu -- Very good post.

@Cris455 -- A much more basic question...

What value or features do you think VirtualBox Additions will bring to the table for you? 

You said your guest is "Ubuntu Server" (Console based), the only feature of VBox guest additions that it would add would be for shared folders. All the other features of are targeted for GUI based Desktop Edition Guests.

Just curious.

---

