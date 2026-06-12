---
title: "Posting terminal output in the forum"
date: 2011-04-23
forum: Security
---

### Post by ClientAlive on 2011-04-23
I've done some searching on googlubuntu for and answer to this but haven't found anything.

As a Linux newbie I was wondering if there are certain types of output from the terminal I should beware of posting for everyone to see? Also are there any codes; that, if I were to be asked to run and report the output on, should raise a red flag?

Thanks in advance.
:D

---

### Post by dacoolio on 2011-04-23
As a general rule, don't run anything on your computer unless you have a pretty good idea of what is going to happen. This is especially true if running something as root. In that case, I would suggest you know EXACTLY what each part of the command does. I'm always careful running anything with * in it. Another thing to be especially careful with is something like dd. 

As for output, most stuff is actually ok. Obviously, don't go posting the contents of your /etc/shadow file or other blatantly personal pieces of data. Another thing to be careful of is some types of debugging information like coredumps, which can sometimes contain data you wouldn't want people knowing. The moral of the story here I guess would be to look at what you're giving to others, and think what someone could do with it if they were bent on attacking you/your computer.

Hope that helped

---

### Post by ClientAlive on 2011-04-23
> **dacoolio said:**
> As a general rule, don't run anything on your computer unless you have a pretty good idea of what is going to happen. This is especially true if running something as root. In that case, I would suggest you know EXACTLY what each part of the command does. I'm always careful running anything with * in it. Another thing to be especially careful with is something like dd. 

As for output, most stuff is actually ok. Obviously, don't go posting the contents of your /etc/shadow file or other blatantly personal pieces of data. Another thing to be careful of is some types of debugging information like coredumps, which can sometimes contain data you wouldn't want people knowing. The moral of the story here I guess would be to look at what you're giving to others, and think what someone could do with it if they were bent on attacking you/your computer.

Hope that helped


Yes. Thank you. I guess I'm a little worried about how much it is that I don't know. I've learned of a few resources for checking on codes I'm asked to run (like "man", "info" and "whatis"), and I happen to have just read about wildcards (ie: "*"); but I'm sure that isn't nearly enough.

When asking for help on things here, it's often requested to run some command to gather information from the system and post back. I'm sure this is almost always innocent enough and is just in order to help; but, sometimes I wonder what things could be used to crack one's system.

Then you throw in the whole concept of phishing. I'm sure there's someone out there in this world phishing terminal output posted on forums and putting the pieces together to try and hack stuff. Sometimes I even wonder if something as simple as my user name and computer name are a no no (ie: uname@computername $).

Thanks
-------------------------------------------------

Edit: I guess what I'm saying is I'm not sure what people can do. I'm sure there are a lot of people who can do a heck of a lot with very little information. Especially if your (read as "my") computer is not set up very securely to begin with.

---

### Post by dacoolio on 2011-04-23
I know exactly what you mean ClientAlive,

When I first started, I really gave no thought into just running whatever people told me. Looking back, I'm REALLY lucky nothing ever happened.

A lot of information can be posted as long as it doesn't uniquely identify YOU. For example, it would be fine posting "hey everyone, Port 21 on my computer is wide open!", as long as no one was able to personally identify you. Now, if you posting this along with your IP address, this would make it so someone could use this information against you specifically, and had a vector in which to get to you.

If you need to know more about what commands you're being asked to run, try the man pages. The first few lines of the man page should give you a good idea what the command does. Also, don't be afraid to ask what the given command does prior to running it.

---

### Post by ClientAlive on 2011-04-23
> **dacoolio said:**
> As a general rule, don't run anything on your computer unless you have a pretty good idea of what is going to happen. This is especially true if running something as root. In that case, I would suggest you know EXACTLY what each part of the command does. I'm always careful running anything with * in it. Another thing to be especially careful with is something like dd. 

As for output, most stuff is actually ok. Obviously, don't go posting the contents of your /etc/shadow file or other blatantly personal pieces of data. Another thing to be careful of is some types of debugging information like coredumps, which can sometimes contain data you wouldn't want people knowing. The moral of the story here I guess would be to look at what you're giving to others, and think what someone could do with it if they were bent on attacking you/your computer.

Hope that helped


Yeah. Thanks. Guess I have a lot to learn then and It's important that I do (I do want to). I jsut ran a search on googlubuntu for my user name; and, in a flash, it brings up every post I've ever posted here (right up to the last post in this thread). Wow!

Thanks for the advice. you really gave me a chuckle with your example by the way. Guess I better get back to studying then.
:guitar:

---

### Post by BkkBonanza on 2011-04-24
Be aware that here and any other forums that the admins can see your IP address. I'm not saying any admin here is or would be malicious - just that you should always assume your IP address is known.

The most immediately obvious command to watch out for is "rm" especially with -rf and * included as combinations of that can instantly cause major grief. The most practical rule is to look thru the commands and understand them before running them. This is also good from a learning linux perspective too. 

Also, try to stick to using software from the repos - though this is not always practical it's always better to get programs from a good source rather than random secondary places. I tend to stay away from any of these file download sites that simply list free (and not free) software cluttered with ads. I just don't trust them.

---

### Post by bodhi.zazen on 2011-04-24
Do not post personal or privileged information (user names / passwords).

In terms of running posted code, most code is in general going to be "safe" as these are monitored forms and malignant code is uncommon here and reported fast.

Still, best to understand the code before you run it.

Learn to read the man pages or ask for clarification if you do not understand the code.

This is a great place to start :

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by ClientAlive on 2011-04-24
> **bodhi.zazen said:**
> Do not post personal or privileged information (user names / passwords).

In terms of running posted code, most code is in general going to be "safe" as these are monitored forms and malignant code is uncommon here and reported fast.

Still, best to understand the code before you run it.

Learn to read the man pages or ask for clarification if you do not understand the code.

This is a great place to start :

[http://linuxcommand.org/](http://linuxcommand.org/)


Right on. I'm learning. I can navigate the file system pretty well and make files and directories, pipe stuff, sort of filter stuff, know about man, info and whatis. I'm working on beefing up my understanding of wildcards right now.

Coincidentally, linuxcommand.org is one of my book marks.

I guess what noids me out is the idea that there are people in the world with a heck of a lot greater knowledge than I (right now that doesn't take much). Some of them may be up to no good and I don't want to learn the hard way. Suppose it's better safe than sorry huh? Take the time to research something I'm asked even if it takes longer for me to reply?

Thanks for the support and advice guys.

Oh! I just thought of something! Well, it occurred to me that it might be good not to show the username and computer name in anything I post (ie: uname@computername $). Maybe a good way to do that is pipe the output into a file with less?

What do you think? Is that pretty common practice around here?

---

### Post by Dave_L on 2011-04-24
I normally strip off the uname@computername from output that I post, although that's probably overkill.

I don't run commands that I don't understand.  I'll find out what they do first, either by "man command", searching for documentation about it, or at least asking about it.

It's not too hard to figure out which people are knowledgeable and reliable by reading their previous posts. But even if the person helping you has good intentions, there could be an honest mistake in his instructions.

---

### Post by oldos2er on 2011-04-24
If you're at all unsure about a command someone's asking you to run, ask. Someone's who's genuinely trying to help you out will not be offended by this.

---

### Post by ClientAlive on 2011-04-24
Got ya.

Guess I was thinking about more than just people on the forum though. Sorry if I didn't clarify that better before.

Go to [www.googlubuntu.com](www.googlubuntu.com) and put your user name in the search bar. You'll see every post you've ever put on this forum come up. some or even many of them may contain output from your terminal that you had posted.

Now, lets say for instance there's some evil guy (or gal) in New York or wherever they might happen to be. This person is all about finding someone to rip off so he goes out on the internet looking for a victim. He starts out just looking at who is using the forum and doing regular google search on the ones that look nice and juicy to him until he finds someone who actually has some means. ("means" can mean a lot of things here too but lets move forward with just one example in mind - you'll see). Ahh . . . the perfect victim, he says to himself. Now he comes back to googlubuntu (or whatever other resources there may be) and begins searching on that person and putting together the puzzle pieces.

He finds a post here from two years ago and it has some terminal output posted with a certain piece of information useful to him so he saves that off to the side. Then he finds another post there, this one's from six months ago and it has a different piece of information in it. And this continues. Pretty soon he has all he needs and he uses some software he has to crack your system, get the personal info he needs to rip you off and then does so.

The next time you log into your bank account you find yourself quite surprised. What happened? You will say to yourself. How can this be. What happened is that over the course of time you posted terminal output with little pieces of this and pieces of that in it along the way. All it took was a not so well intentioned person to come along and they had a feast on the smorgasboard of information that was out there.

So what can a person do? The only real possiblity is to not put that kind of info out there in the first place. But what if you are just new to the game and don't really know what is and what isn't sensitive? I mean, let's face it, you don't know how cracking a system is done or what someone else would need to do it.

So, for instance - some of the commands that can be run in your system produce long lists of information but, in reality, only a small part of that list is actually needed to help you with your problem. Take "dmesg" for example. Huge list of items. But are any of them sensitive information? If you're new to the game you may not know. You could learn all about Linux and you would eventually find out but you're running into problems here and there that you want help with and you see right away that this learning thing might take a while. Or how about "lspci"? That's a decent little list of stuff. Not as long as "dmesg" but not too bad. Same thing.

So, under the circumstances, how do you prevent the wrong information from getting out in the first place? You would have to to start early - right? I mean, once it's posted it's posted. So, if you don't know what is and isn't sensitive, you would either have to ask someone who knows what the specific things are or find some book or article that listed them.

If you went with a book, you might hope to find something that is a short read. I mean, let's face it, there are other things about Linux you are more interested in and you're spending a lot of time already studying those things. You might also hope that the book was very focused and gave only the information you needed - you've learned through experience how many hundreds of books there are out there, cluttering up the market. But you'd need some kind of resource or you would be subject, again, to that painfully long learning curve; and, by that time, it could, possibly, be too late. In the end, you might find it a real shame if you were to spend months reading this book and that only to find out that the list of items you really needed to know about was very short.

Thanks guys for exploring this with me. I appreciate it.

Jake
:)

---

### Post by josephmills on 2011-04-24
some of the things that I dont put up or try not to are 
1)IP ADDRESS  
2) passwords (none at all)
3) mac address 
4) anything that I do not know what it is. 
you can also go back to googlubuntu.com type in your user-name and start opening all of your posts. look and see if any of the stuff in the list(1-3) are on any of your posts then go to the **report** and report it to a mod tell them why you want it removed and I am sure it will be gone fast. also if some one is asking you to post something that you do not trust and that you have done research on and know it could be bad then report that person also to a mod show the mod the research that you have come up with. I would say also that as far as your bank goes and using a browser to sign into your bank you can always delete any cookies that are on your system and also all the cache should be deleted now and then. or after signing on to a bank account also look into local security clubs(hackerspaces, 2600, linux user groups ) get invoked i the community in RL I think that that is the fastest way to learn. Hope that this helps

---

### Post by oldos2er on 2011-04-24
> **ClientAlive said:**
> Got ya.

Guess I was thinking about more than just people on the forum though. 
:)

I hear you. And my comment was meant in more general terms too. One thing that bothers me from time to time is, myself or someone else replies to a question from a newbie asking for more info (usually by running one or more commands and posting the output), and the OP never posts back. I can't help but feel that sometimes this is because they are embarrassed by their lack of understanding what was asked and/or how exactly to provide the answer.

Not related to security; just my thoughts.

---

### Post by oldmankit on 2011-04-26
I'm not too paranoid when it comes to this kind of thing.  The thing is, most people on these forums are here to help.  If you go and divulge too much information, they will recommend you remove it.  People look out for each other here, that's why it such a great place to get help.

If you're really paranoid about banking, why not use a live CD every time you want to use your internet banking?  Even if your usual Ubuntu system is compromised (very unlikely as a home user), then it won't matter, because the live CD is like a fresh install every time you use it.

---

### Post by matt_symes on 2011-04-26
Hi

If your really worried, to keep your IP address safe you can always browse with TOR or some other proxy.

I would not get too paranoid. Just keep sensitive data safe such as passwords.

IP addresses and mac addresses are not that important IMO. Just make sure you are behind a decent router with firewall.

BTW: Never put your e-mail address on any forum. 

Kind regards

---

