---
title: "Virtual Box | Host: Ubuntu 14.04, Guest: Win7 | Logitech C910 | Any Use?"
date: 2015-08-28
forum: Virtualisation
---

### Post by anotherman2 on 2015-08-28
Hi!

Sorry if this issue has already been solved, but I could not find anything that would address my question.

Question:

If I managed to access my Logitech C910 webcam in a Win7 guest machine running inside a VirtualBox on a Ubuntu 14.04 guest, would I be able to use the Logitech software to adjust my webcam settings, and would I be able to use the Logitech software's image and sound enhancements (RightLight, RightSound)?

I would love to not have to boot into Windows every single time I want to use this webcam.

Thoughts?

---

### Post by ajgreeny on 2015-08-28
Have a search on my custom ubuntu-based google search page, [https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao](https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao) , using search term Logitech C910 webcam and you will get a lot of possible answers to this, which I regret I don't have time to search through.

Very often Logitech hardware works with no problem in Linux and Ubuntu; are you certain that camera is not already working?
How have you tried to test whether or not it works so far?

---

### Post by anotherman2 on 2015-08-29
> **ajgreeny said:**
> Have a search on my custom ubuntu-based google search page, [https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao](https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao) , using search term Logitech C910 webcam and you will get a lot of possible answers to this, which I regret I don't have time to search through.

Thank you for the reference. I will check it out.

> **ajgreeny said:**
>  Very often Logitech hardware works with no problem in Linux and Ubuntu; are you certain that camera is not already working?
How have you tried to test whether or not it works so far?

The camera works alright, and that is not the issue I am having.  I am wondering about the following:

>  
If I managed to access my Logitech C910 webcam in a Win7 guest machine  running inside a VirtualBox on a Ubuntu 14.04 guest, would I be **able to  use** **the Logitech software** to **adjust my webcam settings**, and would I be**  able to use** the **Logitech software's image and sound enhancements**  (**RightLight**, **RightSound**)?


---

### Post by ajgreeny on 2015-08-29
Oh, sorry, I think I misunderstood.

If the software for changing the settings of the webcam is for Windows you should certainly be able to make the changes using that and they should then be usable in Windows, but I doubt that any changes made will stick once the VM is closed and Ubuntu takes over the webcam.

Worth trying, I think, but I don't hold out much hope.

---

### Post by anotherman2 on 2015-08-29
> **ajgreeny said:**
> Oh, sorry, I think I misunderstood.

No problem at all. Thanks for taking the time to respond!

> **ajgreeny said:**
> 
If the software for changing the settings of the webcam is for Windows you should certainly be able to make the changes using that and they should then be usable in Windows, but I doubt that any changes made will stick once the VM is closed and Ubuntu takes over the webcam.


My intended use case would be: Whenever I intend to use my webcam, I do not have to reboot into Windows, but simply start the VM and use it within the VM for video chat or recording.

I use my camera professionally, and I am just not really happy with the lack features in Ubuntu. Basically all I can do is access the camera and microphone. No way to adjust anything (orientation, zoom, etc.), and I lose RightLight and RightSound, which I do find very useful.

BTW - do you know of a single high-quality webcam that would work completely - settings, enhancements and all - under Ubuntu?

---

### Post by SeijiSensei on 2015-08-29
Have you tried using [cheese]("https://apps.ubuntu.com/cat/applications/precise/cheese/")?  It's in the repositories.  It may not have all the settings you wish to use though.

Another option is to install wine in Ubuntu, then install the Logitech software into that.  I haven't used wine much and not with USB devices, but you could give that a try.

---

### Post by ajgreeny on 2015-08-29
There was a time, not so long ago, when USB devices and wine did not play together at all.  I do not know if that has now changed, but I know there was certainly a wish to get it working, so maybe it now does.

As to your query, I still do not know how well that might work to do what you want in a VM but it must be worth trying.

If it is successful please let us know as it will help with future queries that may come along.

---

