---
title: "I'm Gone..."
date: 2008-06-16
forum: Testimonials &amp; Experiences
---

### Post by SCURVER on 2008-06-16
Well...I still cannot send or receive mail using Evoluton and cannot load or run Thunderbird, so it's time to go; a few final questions, although will not need any reply from this forum as few of my questions were ever answered by this group. Strange, I can load and run Firefox easily from XP and the same for Thunderbird. Why isn't it as easy to do that with UBUNTU? And never could install and run additional programs; could download them alright, but nothing else, and that is something very easy to do in XP. I don't like XP as it crashes far too often (not that UBUNTU doesn't crash, too, but.......I like the LINUX philosophy and I share that; but first and foremost, if one is running a computer, one needs to be able to run programs on it and this I cannot do with UBUNTU. LINUX is all the same in that regard, it seems to deliberately make using that O.S. difficult. WHY??? I read instructions and a book about LINUX and UBUNTU and when I try to employ what I've read, it WON"T work! It will NOT work! I ask for help in the forums and get nothing. This is one strange place.

                                   SCURVER

---

### Post by powerpleb on 2008-06-16
Did you try the Add/Remove Programs option in the menu? That is the way you install software in Ubuntu, no need to hunt for it and download it. Linux is actually a lot easier when it comes to installing software, you just have to get over the fact that it works differently.

---

### Post by st33med on 2008-06-16
Woah, woah, woah!!! Calm down, just tell us why you can't run Firefox. What errors are you getting (if any at all). How about doing this in the terminal:
```
firefox
```
Does this give errors? Did you install from the repos through synaptic or aptitude?

---

### Post by fr.theo on 2008-06-16
I have had the same problems, but there are ways around a lot of the troubles that the system has, in my opinion its half the fun.

I have had problems from my modem to scanners to running programs and things as simple as dvds.

however If I can help you figure out some of them, I will try my best.


Kind regards 

FR. T.

---

### Post by ravenvii on 2008-06-17
Except for very few cases, you're not supposed (or should, for that matter) to download programs to install. You use apt-get (or Synaptic) to install programs.

It's just different from Windows. You have to think differently to get it. Thunderbird works exactly the same in Windows and Linux. Simply run Add/Remove (or Synaptic, same thing different GUI), and search for Thunderbird. Tick that box, and click Apply. Boom! You have Thunderbird somewhere in your applications menu (in one of those obvious folders... Internet I think it would be). Run it, and that's it. You're in familiar territory.

(Alternatively... in terminal: "sudo apt-get install thunderbird"... type your password... once it finishes, "thunderbird". :) )

---

### Post by brnetonboy on 2008-06-17
I am new to Linux too and I must admit I feel the same way. As someone who knows his way around a XP box, it seems like linux is "dumbed down" way too much for the average somewhat-knowledgeable person. You either have to be a computer idiot or a guru. Instructions leave out BASIC assumptions that are not at all obvious to a new person, and when you ask for help, you get specific suggestions but nobody explains the basic assumptions you're missing or takes the time to elaborate on how things really work. 

I personally started about 20 threads across the internet, over the course of a few months, trying to figure out how you can know what a desktop shortcut points to.

But after months and months of stupid nonsensical answers, I finally realized it on my own: shortcuts don't point to files like they do in windows. They just have the name of the program in them, and they run the program, as if you type it in the command prompt.

My advice is to stick around these forums just a little longer--I understand you're going back to windows, but I bet I can answer your questions! I promise, I'll actually read your question all the way through and answer the question you ask (unlike most people seem to do). Just give the forums another chance. There are some people who can and will help if you just give a little more time...

---

### Post by powerpleb on 2008-06-17
> **brnetonboy said:**
>  I finally realized it on my own: shortcuts don't point to files like they do in windows. They just have the name of the program in them, and they run the program, as if you type it in the command prompt..
Symbolic links point to files in Linux.

To create one in Nautilus right click on a file and click "make link"

or in the terminal type
```
 ln orginal.file link.file
```

---

### Post by brnetonboy on 2008-06-17
> **powerpleb said:**
> Symbolic links point to files in Linux.
To create one in Nautilus right click on a file and click "make link"

ahh... Nautilus is the file manager--like windows explorer--that shows all the folders and stuff. Took me a while to figure that out. 

Anyway--that works great--you can right click on the link, go to "properties" and it says right there "Link target: blablabla" which is fine!

But what about links that you didn't create like that? For example, there is a Firefox link on my desktop too. Go to *it's* properties and there is NO "Link Target" anywhere...

I appreciate your help. But I do want to point out that this is the sort of thing that the Original Poster and I have been frusterated with: somebody says "looks its' easy do ABC" but it is no help at all because it only works in that very specific circumstance, and if I ever want to do ABCD or AB2C, or any slight variation, the help is useless because as the OP said, 
> 
I read instructions ... and when I try to employ what I've read, it WON"T work! It will NOT work!


Now I am willing to take the time to figure it all out on my own--actually a lot of it can be fun. But it would be neat if we could figure out how to see things from the noobs perspective (don't assume we know what "nautilus" or "symbolic link" means) and give information that is helpful on a slightly broader scope, for average non-idiot/guru people.

Again--not meaning to be ungrateful or insulting in any way--I have gotten a lot of help here, and I think everyone is trying their best to help everyone else, which is WONDERFUL. But there is still something to be desired. Also, people who want help shouldn't get upset and leave so quickly. I'm sure the OP won't ever come back to this thread and take advantage of all the people willing to help him out...

---

### Post by stchman on 2008-06-17
> **SCURVER said:**
> Well...I still cannot send or receive mail using Evoluton and cannot load or run Thunderbird, so it's time to go; a few final questions, although will not need any reply from this forum as few of my questions were ever answered by this group. Strange, I can load and run Firefox easily from XP and the same for Thunderbird. Why isn't it as easy to do that with UBUNTU? And never could install and run additional programs; could download them alright, but nothing else, and that is something very easy to do in XP. I don't like XP as it crashes far too often (not that UBUNTU doesn't crash, too, but.......I like the LINUX philosophy and I share that; but first and foremost, if one is running a computer, one needs to be able to run programs on it and this I cannot do with UBUNTU. LINUX is all the same in that regard, it seems to deliberately make using that O.S. difficult. WHY??? I read instructions and a book about LINUX and UBUNTU and when I try to employ what I've read, it WON"T work! It will NOT work! I ask for help in the forums and get nothing. This is one strange place.

                                   SCURVER

Funny, I can run Evolution, Firefox, Thunderbird on many machines with no problems.

---

### Post by ad_267 on 2008-06-17
It sounds like you're trying to install applications by downloading them from the internet. If you've read books on Ubuntu you should realise that's not how you do things. Just install the thunderbird package using your favourite package manager (synaptic, apt-get, aptitude) and it should work perfectly.

---

### Post by anthonie on 2008-06-17
@SCURVER

I do not know what your problem looks like exactly as I only logged on to the forum to quickly solve a problem I encountered this morning. By the tone of your message I'd say you ran into more than one problem. 

However, from the post in this thread, very little information can be derived. So my advice would be, if you want a little help solving a problem, understanding it and finding a solution, you should start with a proper description of the problem. That, I did not see in your post. 

Another thing I found a bit awkward, to say the least, is that you decide to switch back to another OS because you have some problems with an application. To me, that sounds counter-intuitive. If the OS itself is working (And Ubuntu has gone through tremendous efforst to make the OS install as easy as possible) I don't get why you would switch back to another OS because one or two things are not working on an application-level.

Just my two cents...

---

### Post by hyper_ch on 2008-06-17
bye ):P

---

### Post by manishanchan on 2008-06-17
I have never come through it.well i will definately come across  that sooner  and ill definately let u know by others.

---

### Post by bmac on 2008-06-17
> a few final questions, although will not need any reply from this forum as few of my questions were ever answered by this group.

Odd, your posts indicate that you've been responded to multiple times and yet you continued to ignore the individuals that attempted to assist you. Even in this your so called final post, individuals are endeavoring to assist you... 

> I ask for help in the forums and get nothing. This is one strange place.

Perhaps what is strange is your continuing effort to rant about that which you don't understand and have no desire to learn.

I don't believe you will even return to read the responses from this posting and can only hope the admin. closes it.....

---

### Post by Keyper7 on 2008-06-17
I agree. People, stop wasting your time on this thread. Take a peek at the OP's history: he never replied to the people who tried to help him (except on **one** out of several threads he created) and never was more descriptive than "I have a problem. Help.". Furthermore, he's bitching and whining about the forum despite the fact that **all of his threads have been replied to**. This and the fact that he explicitly said that he won't be back are good enough reasons to close this thread.

To brnetonboy:

There are several ways to get help from the community. If you are having problems with basic concepts, you could try the IRC channels, where you can get quick help and immediate responses to any aditional doubts. People will always have difficulty in assimilating something they're not used to. A person who used Linux or Macs his entire life will not realize at a first glance what the hell the words "explorer" and "shortcut" mean.

---

