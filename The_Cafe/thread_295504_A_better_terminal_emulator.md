---
title: "A better terminal emulator"
date: 2006-11-08
forum: The Cafe
---

### Post by grizzly on 2006-11-08
First  the disclaimer: I love the cli interface and use it ALL the time! But IMO it can be much better with regards to giving me information at once.

Here's a quick pic of what I am looking for : [http://h1.ripway.com/chesss/dirlist.png](http://h1.ripway.com/chesss/dirlist.png) . Basically what I want is lots of information from the screen at a glance without having to type anything or more importantly without having to give up my prompt .

For example; If I am in the middle of writing 'ls | egrep Search* | xargs mv --target-directory=..which was that folder?'

Similarly wouldn't it be nice to have constant list of *.rb files . This would prevent having to type ls all the time, guess if some-file had caps same , or press 'tabs' to check if a particular file exists or exists in some sub-folder and so on.

Anything like this somewhere or any other alternatives?

---

### Post by xtacocorex on 2006-11-08
You could try Midnight Commander, it's a terminal based filemanager. It might do most of what you want to do, but I'm not sure as I haven't ever used it.
Here is a screenshot: [http://www.ibiblio.org/mc/images/mc-panels.png](http://www.ibiblio.org/mc/images/mc-panels.png)
I do know that the program is in the repositories, so it won't be hard to install.

---

### Post by grizzly on 2006-11-08
I don't think mc is what I am looking for, though I haven't exactly 'used' mc. Can I still use the terminal normally with mc

---

### Post by PapaWiskas on 2006-11-08
> **grizzly said:**
> I don't think mc is what I am looking for, though I haven't exactly 'used' mc. Can I still use the terminal normally with mc

In short yes.

Here is a snippet from the Midnight Commander website that should give you an overview albeit briefly.

"GNU Midnight Commander is a user-friendly yet powerful file manager
   and visual shell, useful to novice and guru alike.  It provides a
   clear, user-friendly, and somewhat protected interface to a Unix
   system while making many frequent file operations more efficient and
   preserving the full power of the command prompt.  After some
   practice, you will wonder how you could ever live without it."

---

### Post by B0rsuk on 2006-11-08
> **grizzly said:**
> I don't think mc is what I am looking for, though I haven't exactly 'used' mc. Can I still use the terminal normally with mc

It's like Norton Commander or Total Commander. It may be what you're looking for. By default you don't get the feedback when you type commands in MC, but you can always press ctrl-o to switch.

---

### Post by grizzly on 2006-11-08
> press ctrl-o to switch. Ah! thats it!! Thanks a lot. 
Its still not 'at a glance', but the the next best thing.

---

### Post by grizzly on 2006-11-08
Another thing, how to start mc with every interactive shell in a 'minimized mode'. 
Anybody using fdclone? I am trying it alongside mc and I quite like it, and would probably use it full time, but it doesn't seem to have anything like mc's ctrl+o to switch instantly.. 

it does have its own..er.. 'typing area', but its not quite intuitive and needs 2 'enters' for one command.

---

### Post by grizzly on 2006-11-14
I found a GREAATTT SOLUTION!!

The killer app being viewglob! This does exactly what i had in mind, i.e it shows the files/folders of a directory automatically after every 'cd' and even after tab completion!! works with bash and zsh
Infact I would call it a compulsory thing for a shell. Check my sig for a screenshot.

---

### Post by grizzly on 2006-11-14
Oh great I can't have a signature, coz I had the line 'religion is harmful' in my signature! I had removed the line but some mod who thought the muslim countries who force everyone to 'donate' money in mosques are an examlpe of tolerance(yes theses were his exact words)!!! :lol: , has apparently it seems removed my ability to have any signature..  
Anyways here's a [screenshot](http://h1.ripway.com/chesss/viewglow.png) of viewglob - a must with bash!!

---

### Post by hkgonra on 2006-11-14
I swear , every time I see someone talk about a terminal emulator I am thinking about IBM client access or something along those lines.

---

