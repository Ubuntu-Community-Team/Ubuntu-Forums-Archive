---
title: "Is there a way to see what files were opened?"
date: 2011-08-10
forum: The Cafe
---

### Post by TheNessus on 2011-08-10
Hmm, well I was away, and I know that my computer has been used. Not that I'm paranoid or anything, but I am curious to see which files were opened. Specifically, I'm talking about photos. I saw that in "recent files" (gnome) some pics were opened that I didn't open, while I was on vacation. But the list is too short, more were possible viewed.

Is there a log in some .rc file somewhere that shows more than what "recent files" merely show? 

thanks

---

### Post by Basher101 on 2011-08-10
instead of being paranoid i would simply tighten security (e.g. better passwords..) or is your computer used by your family?

---

### Post by TheNessus on 2011-08-10
> **Basher101 said:**
> instead of being paranoid i would simply tighten security (e.g. better passwords..) or is your computer used by your family?

I'm not worried about security. I am simply curious to see what was looked at. The "culprit" is my girlfriend, she already has my passwords :)

---

### Post by haqking on 2011-08-10
> **TheNessus said:**
> Hmm, well I was away, and I know that my computer has been used. Not that I'm paranoid or anything, but I am curious to see which files were opened. Specifically, I'm talking about photos. I saw that in "recent files" (gnome) some pics were opened that I didn't open, while I was on vacation. But the list is too short, more were possible viewed.

Is there a log in some .rc file somewhere that shows more than what "recent files" merely show? 

thanks


ls -lt 

will list files with most recently accessed first, look for dates from when you were away

---

### Post by haqking on 2011-08-10
> **TheNessus said:**
> I'm not worried about security. I am simply curious to see what was looked at. The "culprit" is my girlfriend, she already has my passwords :)

Giving passwords out especially to Girlfriend is abyssmal ;-)

Ask her what she accessed ? if you dont want her to know or you think she will lie then no trust, if no trust why share passwords ?

---

### Post by Basher101 on 2011-08-10
> **haqking said:**
>  if you dont want her to know or you think she will lie then no trust, if no trust why share passwords ?

That really doesnt make sense. Curious how you want to deal with it tho. I would ALWAYS be careful when it comes to trust questions with girlfriends...

---

### Post by haqking on 2011-08-10
> **Basher101 said:**
> That really doesnt make sense. Curious how you want to deal with it tho. I would ALWAYS be careful when it comes to trust questions with girlfriends...


like i said ls-lt will show files accessed from with most recent first.

doesnt make sense ?

i meant why not ask her what she accessed ?

---

### Post by northwestuntu on 2011-08-10
if shes asks, just tell her you don't know how those photos on there ;)

---

### Post by TheNessus on 2011-08-10
lt -ls doesn't seem to work, or at least I don't know how to use it...

I get this:
```
essus@nessus-Inspiron-N3010 ~ $ ls -lt
total 204
drwxr-xr-x 4 nessus nessus   4096 2011-08-10 12:57 Downloads
drwxr-xr-x 2 nessus nessus   4096 2011-08-10 12:56 Desktop
-rw-r--r-- 1 nessus nessus 158394 2011-07-24 12:32 Screenshot.png
-rw-r--r-- 1 nessus nessus      0 2011-07-20 12:21 output.pdf
drwxr-xr-x 3 nessus nessus   4096 2011-07-15 11:15 Pictures
drwxr-xr-x 3 nessus nessus   4096 2011-07-15 11:15 Videos
drwx------ 7 nessus nessus   4096 2011-07-14 11:34 Dropbox
drwxr-xr-x 2 nessus nessus   4096 2011-07-05 23:23 scripts
drwxr-xr-x 3 nessus nessus   4096 2011-06-29 14:09 VirtualBox VMs
drwxr-xr-x 2 nessus nessus   4096 2011-06-22 14:25 Documents
drwxr-xr-x 2 nessus nessus   4096 2011-06-22 14:25 Music
drwxr-xr-x 2 nessus nessus   4096 2011-06-22 14:25 Public
drwxr-xr-x 2 nessus nessus   4096 2011-06-22 14:25 Templates
-rwxr-xr-x 1 nessus nessus   1373 2011-05-20 17:35 skype-notify-messaging
```


I have pretty much full trust in my gf, it's why I share my passwords, if say I need her to access stuff (with my guidance, using Ubuntu is "too weird" for her to handle) when I can't on my own, or stuff. 
I still am curious to know what she looked at. And no, I have nothing embarrassing, or stuff I keep from her, there. asking her is... not desirable.

---

### Post by Copper Bezel on 2011-08-10
Guys, it's not serious. He's curious. She was snooping and he's snooping back. 

Thanks for the command, though, haqking - that could be useful in the future.

Edit: TheNessus, navigate to a folder you're curious about in the terminal and run ls -lt -R to see all the access times for the files inside, or omit -R to just look at files and subfolders in the root of that folder.

---

### Post by wojox on 2011-08-10
lsof is a command meaning "list open files"

---

### Post by haqking on 2011-08-10
> **TheNessus said:**
> lt -ls doesn't seem to work, or at least I don't know how to use it...

I get this:
```
essus@nessus-Inspiron-N3010 ~ $ ls -lt
total 204
drwxr-xr-x 4 nessus nessus   4096 2011-08-10 12:57 Downloads
drwxr-xr-x 2 nessus nessus   4096 2011-08-10 12:56 Desktop
-rw-r--r-- 1 nessus nessus 158394 2011-07-24 12:32 Screenshot.png
-rw-r--r-- 1 nessus nessus      0 2011-07-20 12:21 output.pdf
drwxr-xr-x 3 nessus nessus   4096 2011-07-15 11:15 Pictures
drwxr-xr-x 3 nessus nessus   4096 2011-07-15 11:15 Videos
drwx------ 7 nessus nessus   4096 2011-07-14 11:34 Dropbox
drwxr-xr-x 2 nessus nessus   4096 2011-07-05 23:23 scripts
drwxr-xr-x 3 nessus nessus   4096 2011-06-29 14:09 VirtualBox VMs
drwxr-xr-x 2 nessus nessus   4096 2011-06-22 14:25 Documents
drwxr-xr-x 2 nessus nessus   4096 2011-06-22 14:25 Music
drwxr-xr-x 2 nessus nessus   4096 2011-06-22 14:25 Public
drwxr-xr-x 2 nessus nessus   4096 2011-06-22 14:25 Templates
-rwxr-xr-x 1 nessus nessus   1373 2011-05-20 17:35 skype-notify-messaging
```
I have pretty much full trust in my gf, it's why I share my passwords, if say I need her to access stuff (with my guidance, using Ubuntu is "too weird" for her to handle) when I can't on my own, or stuff. 
I still am curious to know what she looked at. And no, I have nothing embarrassing, or stuff I keep from her, there. asking her is... not desirable.


i said ls -lt not lt -ls

anyways you got it to work.

which shows you the downloads and docs directory were accesed today.

I suspect it is in your docs folder you are concerned about ?

in which case do the same in that directory.

you could of course also do a recursive ls.

there might be a simpler way to do this.

@ wojox

the OP asks for files opened when he was away not files that are currently open

---

### Post by haqking on 2011-08-10
perhaps this might work but you will need to play with the find command to specify dates.

find /home/nessus/Documents -iname "*.*" -atime -5 -print

this will show all files accessed over last 5 days, you could also pipe it to a txt file is you want, and change Documents folder to suit focus

i am trying to figure out how to use a specific date right now though, unless anyone else has input on that

---

### Post by haqking on 2011-08-10
you could also add the last accessed column to nautilus for a particualr directory like documents etc and see if anything was accessed on a given date ?

---

### Post by koleoptero on 2011-08-10
If you have zeitgeist installed you can use the activity journal to see exactly what and when has been opened.

---

### Post by TheNessus on 2011-08-10
> **koleoptero said:**
> If you have zeitgeist installed you can use the activity journal to see exactly what and when has been opened.
I do. Do you know how I can reach that?


Thanks to others too, I am working on those as well.

---

### Post by Copper Bezel on 2011-08-10
I was assuming Zeitgeist isn't installed, or else this wouldn't be a question. = )

You might have the framework installed but not the activity journal. You want the package gnome-activity-journal. Launch it and you'll have everything you need at a glance.

[QUOTE=haqking]find /home/nessus -iname "*.*" -atime -5 -print[/QUOTE]
Better to do it for individual folders. Doing it in ~ is going to bring up all kinds of irrelevant temp and config junk.

---

### Post by haqking on 2011-08-10
> **Copper Bezel said:**
> I was assuming Zeitgeist isn't installed, or else this wouldn't be a question. = )

You might have the framework installed but not the activity journal. You want the package gnome-activity-journal. Launch it and you'll have everything you need at a glance.


Better to do it for individual folders. Doing it in ~ is going to bring up all kinds of irrelevant temp and config junk.


yeah my bad ive edited, i was meant to say that, cheers

---

### Post by el_koraco on 2011-08-10
> **TheNessus said:**
> The "culprit" is my girlfriend, she already has my passwords :)

:D 
Change them and don't tell her!

---

### Post by Enigmapond on 2011-08-10
Zeitgeist, Gnome Activity Journal and the Zeitgeist Manager really do rock especially in searching for a document. I recommend it.  >)

Cheers!

---

### Post by TheNessus on 2011-08-10
> **Copper Bezel said:**
> I was assuming Zeitgeist isn't installed, or else this wouldn't be a question. = )

You might have the framework installed but not the activity journal. You want the package gnome-activity-journal. Launch it and you'll have everything you need at a glance.


Better to do it for individual folders. Doing it in ~ is going to bring up all kinds of irrelevant temp and config junk.

I got exactly what I need. huge thanks.

Now, I know she did look at almost my entire photos folder some two days before I came home. Wonder what that means...

Not that I'd confront her or anything, we're doing better than ever right now... Just interesting, it's all.

---

### Post by Basher101 on 2011-08-10
Maybe she missed you? most plausible conclusion i can think of

---

### Post by TheNessus on 2011-08-10
> **Basher101 said:**
> Maybe she missed you? most plausible conclusion i can think of

Probably. Though there are always any other explanations. I'm not an optimist. I am screwed up, in a way :)

---

### Post by MasterNetra on 2011-08-11
lol I wouldn't give my gf my password, I don't give anyone my password.

---

### Post by pvaughan on 2011-08-18
I see the "Files & Folders" icon on the Launcher will list out the recently opened files in a Dash.  Is there a way to delete the list of recently opened files?  

Many thanks in advance.

---

