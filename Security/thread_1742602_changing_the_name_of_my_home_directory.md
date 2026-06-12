---
title: "changing the name of my home directory"
date: 2011-04-29
forum: Security
---

### Post by ClientAlive on 2011-04-29
I hope this is a good place to post for this. I wanted to come somewhere where I thought I'd run into people familiar with this type of thing.

I'm using Ubuntu 11.04 by the way.

Ok, so, playin' with fire - once again . . .

Started out tonight I wanted to change my user name. Got that sorted out. Had to jump through a few hoops but got it done. Then, of course, I needed to change the group name - same thing, and it's done now. Now I see that my home directory is still under the previous name, so, I start to reason, "I can just use "mv" command to rename it." So I go back into my other user I had created with admin privileges; so I log back into that account, go into the terminal and give it a try. Everything seems to go beautifully! Until I try to log back in as myself . . . All hell breaks loose. Error messages here and error messages there . . . [sigh]. So I go back and change the name back and I'm in as myself again, no prolems.

The thing is though - I still want to change that name.

Can anyone help? Is it a real hassle? I'm very, very determined that this needs to happen, I just hope I don't need to wait till I have a PhD in computer science to accomplish it. That could be a while, since I'm not even in college for it.  :)

Any help would be greatly appreciated.

Thanks

---

### Post by mikewhatever on 2011-04-29
You also have to chmod and chown the files inside the home directory. Use a live cd or the recovery mode.

```
sudo chown -R user:user /home/user
sudo chmod -R user:user /home/user

```

Obviously, substitute your current username to the generic 'user' above.

---

### Post by ClientAlive on 2011-04-29
> **mikewhatever said:**
> You also have to chmod and chown the files inside the home directory. Use a live cd or the recovery mode.

```
sudo chown -R user:user /home/user
sudo chmod -R user:user /home/user

```

Obviously, substitute your current username to the generic 'user' above.


Do you mean that in addition to renaming the home directory I need to change the name of the owner of the tiles and directories inside and also the the permissions to that name?? I just happen to get to the part talking about chown and chmod but don't really grasp it fully yet. In my book I mean.

Thanks

---

### Post by sisco311 on 2011-04-29
You can change a user's home directory with the usermod command: 
```
usermod -md /home/new user
```

For details check out its man page:
```
man usermod
```

---

### Post by ClientAlive on 2011-04-29
> **sisco311 said:**
> You can change a user's home directory with the usermod command: 
```
usermod -md /home/new user
```

For details check out its man page:
```
man usermod
```


I'm reading that man page right now but it makes it sound like there's a whole bunch of things that need to happen to make a complete change over. Unless that "-R" modifier (from post #2) makes the command apply to everything (recursive?). Just want to understand what I'm getting into here so I don't run into problems accessing my own files or services. Am I going to have to go in an manually change all kinds of things? Chrontabs? I saw something about that in this man page and another one I can't remember which.

Thanks.
---------------------------

Edit: I just had an idea. Would it be easier to back up all of the contents of the directory, delete that directory, create a new one under the name I need it to be then move the contents back in? Or would that put me in the same place I am now anyway?

Thanks

---

### Post by movieman on 2011-04-29
> **ClientAlive said:**
> Do you mean that in addition to renaming the home directory I need to change the name of the owner of the tiles and directories inside and also the the permissions to that name??

Only if you changed the user id. Linux attaches the user id to the files, not the user name, so changing the name but not changing the id won't cause any problems.

---

### Post by sisco311 on 2011-04-29
> **ClientAlive said:**
> 
Edit: I just had an idea. Would it be easier to back up all of the contents of the directory, delete that directory, create a new one under the name I need it to be then move the contents back in? Or would that put me in the same place I am now anyway?

Thanks

Nope. The path to your user's home directory is stored in the /etc/passwd file.

```
usermod -d /home/new user
```
will change the path to **/home/new**

If you use the -m option, then the command will rename the old home directory as well:
```
usermod -m -d /home/new user
```

Of course, you could edit the passwd file and rename the directory manually, but using usermod is safer.

---

### Post by ClientAlive on 2011-04-29
> **movieman said:**
> Only if you changed the user id. Linux attaches the user id to the files, not the user name, so changing the name but not changing the id won't cause any problems.


> **sisco311 said:**
> Nope. The path to your user's home directory is stored in the /etc/passwd file.

```
usermod -d /home/new user
```
will change the path to **/home/new**

If you use the -m option, then the command will rename the old home directory as well:
```
usermod -m -d /home/new user
```

Of course, you could edit the passwd file and rename the directory manually, but using usermod is safer.


I feel so confused. This is complicated. There's also a lot of pressure. If I screw anything up with something like this I think I could really pay the price. Maybe I have to go back to studying and just wait until I understand more (could be months). It makes me sad to think that but what can I do? I don't understand what is really going on inside the system when I run these commands you guys are offering and I don't understand why. I don't even know if what I've already done has screwed something up with regard to using my home directory. It doesn't seem like it but I don't think Linux is based on what things "seem" like.

All I wanted to do was change the stupid name. Then I find out it's associated with the group so I change that too. Now the home directory wants my attention. What does it take to do something that seems like it ought to be so simple? Then if you screw it up you pay the ultimate price? Oh-my-god. All I know is I've actually noticed three different names in this thing (four if you count the home directory).

One is the name I see on the log in screen. I can change this through the gui under system settings > users and groups. The other is the name I see before the @ sign in the terminal. And the third is the name of the group. The only way I know to see that information is to type "id" in the terminal. Finally there is the name of the home directory which I can see if I type "cd /home; ls" in the terminal. That makes four. On top of all this there is, apparently, files inside the home directory which store this information. So far I've had to do everything one-by-one and it's excruciating. I say a little prayer to God before I hit the enter key every time I type in one of these commands. It's crazy.

Sorry for the rant guys. I'm like _one_ _month_ into Linux and I often find myself more confused when I try to do something than I was when I began. I spend hours trying to accomplish things that should only take minutes. It is very taxing.

Thanks for putting up with me.

Jake

---

### Post by bodhi.zazen on 2011-04-30
> **ClientAlive said:**
> I feel so confused. This is complicated. There's also a lot of pressure. If I screw anything up with something like this I think I could really pay the price.

Jake

My advice is that you try these things in a virtual machine. You can break a virtual machine running in virtual box all you like without affecting you installation.

Once you get a feel for it, and have tested it out, then run the command on your main install =)

---

### Post by ClientAlive on 2011-04-30
Urgent! Please I need help soon! I tried to make these changes and now I can't get back into my regular account/ directory.

Ok. Well, I guess I was just  freaking out a little bit there (in my previous post). So I did a little  more reading on these things and decided to try the method mikewhatever  suggested:

> **mikewhatever said:**
> You also have to chmod and chown the files  inside the home directory. Use a live cd or the recovery mode.

```
sudo chown -R user:user /home/user
sudo chmod -R user:user /home/user

```Obviously, substitute your current username to the generic 'user' above.


So, as best I could understand, I figured there were (at least) two  things that needed to happen. One was to rename the home directory and  the other was to use the "chown" command to change ownership. I spent a a  bit of time thinking about what order this should be done in, since it  seemed this may be important. Finally, I figured I should rename it  first because changing ownership may affect my ability to change the  name after doing so. I did do what I can understand to do but still have  run into a problem. As it stands I am writing this to you logged in as  my other user I created for doing this task and can not log into my  regular account. I'll explain.

So here is what I did:

First  of all, I noticed that in the code I was given it says: " . . .  user:user . . . " but from what I've read it might be more like " . . .  user:group . . . " this latter is the understanding I went off of. The  name of my group and username (the new ones) are identical to one  another though so I don't think it would've made a difference.

So  I restarted and logged in as my other user named "temporary" who I had  given administrative privileges to. Opened a terminal and ran three  lines of code - one and then the other and then the other.

First:

```
 cd /home; ls
```This  put me in the home fulder under root and showed me the contents. I saw  the home directory in there, under the old name (the one for my regular  account that I was trying to work on).

Next:

```
sudo mv olddirectoryname newdirectoryname
```This renamed the directory to the name as I had perviously changed the user name to (the new one that it is now) (in the other/ regular account).

Finally

```
 sudo chown -R newusername:newgroupname /home/newname
```From  what I understand this changed the ownership of both the user and the  group to the same name as the user and group name I had previously  changed to (the new one that it is now)

Now I attempted to  restart and log in under my normal account (thinking everything would be  fine). Here is why I thought this would be enough and that it would be  ok:

I did see that I was instructed to use the command "chmod" as  well but I didn't understand how this was connected to my task/ goal. I  thought that maybe a mistake was made in that instruction I was given  and here is why I thought that. What I had read was that "chmod" changes  the permissions of files with regard to the three areas "owner" "group"  and "world".  But I though this was generic so that the owner is the  "owner". That if you changed the owner with "chown" he would assume the  "owner" that is that permission/ those permissions.

I had also  read how octal (notation?) or symbolic notation is used after "chmod" to  specify the "rwx" values for each section respectively but none of that  was given in the instrucions I was given. I was confused about this.

So  the bottom line at this point is that I don't understand what it is  that I would change these to from what they already are since what they  are is the default values from when I installed Ubuntu. And I don't  understand if I will be either compromising the security of the files or  effecting my own ability to access/ do whatever with them - if I did  change any permissions with "chmod". I also don't understand how this is  connected to what I'm trying to do. What I do know is that I am unable  now to log into my normal account and I don't have much time before I  need to do so. I have work related material there and will be needing it  soon.

After entering my password when I tried to log back into  my normal account I was given a series of three error messages which I  wrote down on paper. Here is what they were:

"Could not update ICEauthority file /home/olddirectoryname/.ICEauthority"

I clicked "OK" and another came up behind it:

"There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

I clicked "OK" and another came up behind it:

"Nautilus could not create the following required folders: /home/olddirectoryname/desktop,/home/olddirectoryname/.nautilus

After  this I logged back in to the other account named "temporary" I had  created to do this job. I can still log into is (I'm writing to you from  this account now). I remembered that I was instructed to use the  "chmod" also and made an attempt to do so but I don't think I did it  right. Here is the output from the terminal for that attempt.

```
~$ cd /home; ls
buildd  Desktop  lost+found  newdierctoryname  temporary
temporary@computername:/home$ sudo chmod newusername:newgroupname /home/newdirectoryname
[sudo] password for temporary: 
chmod: invalid mode: `newusername:newgroupname'
Try `chmod --help' for more information.
temporary@computername:/home$ chmod --help
```I  sure hope someone sees this soon and can help me. Please, please, if  you see this help. And please, please give a little detail so I can  understand what I need to do. I'm so new to this I'm afraid that if I  don't understand what I'm trying to do I'll make a mistake.

I  suppose I could go as long as 24 hours before I need to access my work  stored in that directory (I return to work on Monday) but it also has  everything I care about and do in it. I'm just sitting here with this  empty directory under my mock "temporary" user.

Someone please help soon.

Thanks you.

---

### Post by CharlesA on 2011-05-01
Are you able to boot into recovery mode and and change the path to your user's home directory?

```
usermod --home /path/to/new/home/ username
```

If you boot into recovery mode (single user mode) you'll get a root prompt so you don't need sudo.

See if that fixes the problem. It sounds like the other user is still pointing to their old home directory.

---

### Post by ClientAlive on 2011-05-01
> **CharlesA said:**
> Are you able to boot into recovery mode and and change the path to your user's home directory?

```
usermod --home /path/to/new/home/ username
```If you boot into recovery mode (single user mode) you'll get a root prompt so you don't need sudo.

See if that fixes the problem. It sounds like the other user is still pointing to their old home directory.


Also see "Edit" at the end of this.

CharlesA, I'm sorry I went mia for a bit there. I've been working on this thing for the last 2 hrs. It turns out I had selected to encrypt my directory when I did the install. I was given the following link to directions - to manually recover data here:  [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually") I have a friend from here who talked with me in chat to help me. He is gone now and I'm sort of back where I started (except for learning how to do what is in those instructions).

Our plan was to try to get into that encrypted directory and copy the personal data out then just remove the entire directory and create a new one. I made it through the steps in the instructions and was at the location: "/home/username/Pirvate". What I saw there could only be revealed by using the "ls -la" command. "ls" responded in a way that would lead one to believe it was empty. After entering "ls -la" what I saw was that there were two dot files. One was owned by root and was the single dot "." the other was owned by username and was the double dot ".." Because of how the "cd" command works if I were to enter "cd .." it would move me up into the parent directory. That is not what I needed at that point. I tried "cd "..""  In other words, the "cd" command with the two dots quoted. It didn't change anything. I found myself right where I was. I am certain that this directory is in tact and that my data is in there. The issue is just accessing it and getting it copied out.

What I think I should try to do is reverse what I had done that led to this and try to log back into that account. My regular account. What I did to get in this mess was: change the directory name and change the ownership on the directory recursively. I believe if I change those two things back I will be able to log back in to the account.  I will be back to were I started before attempting this mess. If it works I will still want to accomplish this goal but I will probably look for a better way (hindsight - ha ha).

It's 2:06 am here. I can't make it much longer but I need to get this fixed right away and badly. Don't know if there is anyone here at this hour or if they will see this that they might advise me. I need to move forward. I'll wait 10 min to see if I get a response but then I need to go on. I pray to God that either someone sees this and comes along to help or that my plan works without causing further damage.

Thank you so very much for your help.

Jake
--------------------------------------

Edit: During the course of following those instructions at the link I was logged in as root via the "suto -i" command.

---

### Post by CharlesA on 2011-05-01
Encrypted directories are a bit of a pain.

basically, all your info is stored in /home/username/.Private (any file starting with a dot (.) is hidden by default).

You need to mount it per the instructions on that page. Was it able to be mounted?

---

### Post by ClientAlive on 2011-05-01
> **CharlesA said:**
> Are you able to boot into recovery mode and and change the path to your user's home directory?

```
usermod --home /path/to/new/home/ username
```If you boot into recovery mode (single user mode) you'll get a root prompt so you don't need sudo.

See if that fixes the problem. It sounds like the other user is still pointing to their old home directory.


I'm sorry. I'm a little ovewhelmed right now but I'm trying to keep it together. I had not addressed your response:

As with most everything else. I do not know what booting into recovery mode is or how it works. I am perfectly willing to use any and all means to ensure I get this resolved but I don't want to abandon a particular direction before exhausting it - unless I understand where the alternative is going to lead. Without knowledge it is difficult to make wise decisions. You didn't know what I was working on until my previous post - I understand. Based on my level of knowledge everything is brand new to me. The wisest decision I know how to make at this juncture is to pick a possible solution, delve into it, and continue until all possibilities are exhausted. In the absence of sufficient new information this retains the inertia I have attained with that particular option - with the hope of reaching an end. This is not meant to be taken offensively. This is just straight forward talk in the midst of a critical situation. If you know of an option that is a better solution and can provide me with just enough detail that I can understand what we are trying to get at - I am more than willing. I am simply trying to be economic with my effort and cautious with my severe deficit in knowledge with Linux.

Thank you for your understanding and patience.

Jake

---

### Post by ClientAlive on 2011-05-01
> **CharlesA said:**
> Encrypted directories are a bit of a pain.

basically, all your info is stored in /home/username/.Private (any file starting with a dot (.) is hidden by default).

You need to mount it per the instructions on that page. Was it able to be mounted?


I 'thought' mounting was successful. Now I have closed the terminal window and don't know how to access history if were to need it.

---

### Post by CharlesA on 2011-05-01
> **ClientAlive said:**
> I 'thought' mounting was successful. Now I have closed the terminal window and don't know how to access history if were to need it.
Type "history" and it will list the commands that you have run.

To get into recovery mode, hit escape to get to the grub menu and then select recovery mode.

---

### Post by ClientAlive on 2011-05-01
> **CharlesA said:**
> Type "history" and it will list the commands that you have run.

To get into recovery mode, hit escape to get to the grub menu and then select recovery mode.


Just hit escape. Once with this, browser, the active window and once with the terminal window the active window. Nothing.

I'm currently logged into the other account - of course. Don't know if that makes a difference.

Thanks

---

### Post by CharlesA on 2011-05-01
Right. Forgot to mention that you have to reboot to get the grub menu. Sorry about that.

---

### Post by ClientAlive on 2011-05-01
> **CharlesA said:**
> Right. Forgot to mention that you have to reboot to get the grub menu. Sorry about that.


ok. not sure what to expect after that but i can look on the net for some more info I guess. I assume that I will be able to enter into that directory and that I will have to do whatever I do from the command line? I assume I will have to try and use the "cp" command to copy my important files to the desktop of my other account (named "temporary")?

Even if all that works it is still not the most desirable plan. Its just maybe the most feasible for me. It would be a shame that that directory is just sitting there if there were a way to actually restore it.

---

### Post by CharlesA on 2011-05-01
Once you get the encrypted directory mounted, you should be able to copy the files where ever you want.

I've got to get to bed, but I'll check in in the morning.

---

### Post by ClientAlive on 2011-05-01
> **CharlesA said:**
> Once you get the encrypted directory mounted, you should be able to copy the files where ever you want.

I've got to get to bed, but I'll check in in the morning.


Thanks for everything man. I'll need to learn what the strategy is for mounting (unless it is the same instructions I found before). I'm beat too though. I'm gonna crash out and come back to it in the morning. I hope this thing doesn't shutdown on me in the middle of the night - as it has been randomly shutting down from time to time (possibly over heating). I'll be back here in roughly 8 hrs and ready to do whatever I have to to fix this. Study, google, work, whatever.

Maybe I'll see you here. I'll look for you.

Have a good rest.

Jake

---

### Post by CharlesA on 2011-05-01
Should be the same instructions that you followed before.

---

### Post by ClientAlive on 2011-05-01
> **CharlesA said:**
> Should be the same instructions that you followed before.


Wow! You must not sleep much I just got up but I'm gonna tackle it n a bit here. Soon as I get some coffee made. We'll see what happens.

---

### Post by ClientAlive on 2011-05-01
Isn't there a way to fix the existing home directory in question? Rather than deleting it and making a new one? Wouldn't that be easier and a better option? If I did that would I just go in and manually edit some configuration file and be done with it?

---

### Post by CharlesA on 2011-05-01
You could change your user to point to the new home directory instead of the old one, and see what happens.

Did you already do that? (using the usermod command above)

---

### Post by ClientAlive on 2011-05-01
> **CharlesA said:**
> You could change your user to point to the new home directory instead of the old one, and see what happens.

Did you already do that? (using the usermod command above)


Well, from the top - when I installed Ubuntu and I got to the part about naming your computer and choosing a user name, I didn't really take the time to think about what I would really want. I just wanted to get through the install so I just put in whatever. This was fine with me for a while but there came a point where I wanted to change those things to what I really wanted ti to be. Now it took me several stages to learn this; but, when Ubuntu finished the install, what it does is use that name you chose for three different things - the user name, the group name, and the name of the home directory. As I discovered these things I wanted everything to be named the other name (all three).

I started by using the "usermod" and "groupmod" commands respectively to change those two names. Then, when I learned the home directory was also named the old name, I tried to follow the directions for changing that, that were given in post #2 of this thread - except I don't think I completed the instructions correctly or something. Now I am here at this point.

I thought that by restating these things more succinctly it might help me receive help with this. Although all that is written in this thread tells that story, it is kind of disorganized and spread out - because I was figuring it out as I went.

At this point, there are two things I want to try and accomplish. Ultimately I would like to complete my original goal of having that home directory named the new name and functioning properly under the newly renamed user and group. I think that a step I need to take first, for safety's sake, is to get a copy of my personal data out of that directory and backed up. I should have approached this that way to begin with. It's a tough lesson to learn this way but I am here now and need to deal with what it is.

Thanks

---

### Post by ClientAlive on 2011-05-01
What about this " -d" option with "usermod"? It says here:  [http://linux.about.com/od/commands/l/blcmdl8_usermod.htm](http://linux.about.com/od/commands/l/blcmdl8_usermod.htm)  that is has to do with pointing the user to the login directory or something like that. Could I use:

```
sudo usermod -d /home/nameofdirectory
```to point my user (not "temporary" but my real/ regular account) to that directory? Would this actually solve the issues those error messages were talking about when I tried to login after changing the directory name? In the code above, is it complete or are there elements missing? Could I do it while logged in as "temporary" even though I would be asking that a different user be pointed to a different directory than the one I am logged in under?

It seems logical that the reason I had those problems when I tried to log in to that account after I changed the directory name - is that it was looking for the old directory name and couldn't find it after I had renamed it.

What do you think about all this?

Thanks

---

### Post by CharlesA on 2011-05-01
That's correct. It's trying to access a directory that doesn't exist.

You can use either --home or -d, I prefer using the long names for switches.

---

### Post by ClientAlive on 2011-05-01
> **CharlesA said:**
> That's correct. It's trying to access a directory that doesn't exist.

You can use either --home or -d, I prefer using the long names for switches.


After my previous post I continued to read about that command and to think about what might be going on that's causing the problem at login. I don't want to be too volatile about this by doing things before waiting for a response but I don't know what people's availability is to be responding to this thread and this is something I need to resolve before Monday rolls around. I'm faced with some very difficult decisions regarding whether to wait to see a response - I need the help - or to try to press forward by researching and doing - I need to accomplish this. I'm trying to do both.

After my previous post to this one I continued to research this command and to think about what might be going on that is causing the problem at login. I came to the conclusion that I ought to try and run:

```
sudo usermod -d /home/hewname newname
```I did this and got no complaints from the terminal about it. I assumed the command was executed without any problems. Then I rebooted and attempted to log in under that account. I was given the same series of error messages recorded in post #10 of this thread. I will paste them below.

> After entering my password when I tried to log back into  my normal  account I was given a series of three error messages which I  wrote down  on paper. Here is what they were:

"Could not update ICEauthority file /home/olddirectoryname/.ICEauthority"

I clicked "OK" and another came up behind it:

"There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

I clicked "OK" and another came up behind it:

"Nautilus could not create the following required folders: /home/olddirectoryname/desktop,/home/olddirectoryname/.nautilus[

After  this I logged back in to the other account named "temporary" I had  created to do this job.

If it is possible, if you are willing or able to, I would like to address what each of these mean so that I might diagnose the situation and find a resolution. In addition to fixing the problem I also need to understand how it is being fixed/ working. I'll do all the work and research if you will give me pointer. Ok?

I'm on my way back to the internet to research each of these error messages and explore what options I may have. I will check back here every few minutes or so to see what's going on.

Thanks

---

### Post by CharlesA on 2011-05-01
Check that the home directory is set correctly -

```
cat /etc/passwd | grep username
```

It should look something like this:

```
user:x:1000:1000::[COLOR="Blue"]/home/someuser[/COLOR]:/bin/bash
```

---

### Post by ClientAlive on 2011-05-01
> **CharlesA said:**
> Check that the home directory is set correctly -

```
cat /etc/passwd | grep username
```It should look something like this:

```
user:x:1000:1000::[COLOR=Blue]/home/someuser[/COLOR]:/bin/bash
```


I'm on my way

---

### Post by ClientAlive on 2011-05-01
Results:

```
~$ cat /etc/passwd | grep newname
newname:x:1000:1000:newname,,,,:/home/newname:/bin/bash
temporary@kLy3ntAlyVe:~$ cat /etc/passwd | grep oldname
temporary@kLy3ntAlyVe:~$
```

I ran it for both the new name and the old name (in that order). It appears to me that it is connected with the new name.

---

### Post by CharlesA on 2011-05-01
Hrm that looks right. The shell knows where the correct home directory is, but apparently the GUI doesn't.

I'd suggest renaming everything back to the old name, and seeing if the error goes away.

That way you could at least get your data off the machine.

---

### Post by ClientAlive on 2011-05-01
> **CharlesA said:**
> Hrm that looks right. The shell knows where the correct home directory is, but apparently the GUI doesn't.

I'd suggest renaming everything back to the old name, and seeing if the error goes away.

That way you could at least get your data off the machine.


That is one of the last things I tried to do last night before going to bed. I don't have that history in front of me now but I recall that terminal's response was that it could not "lock" the directory. I don't believe the "user" and "group" renames were successful.

Here is a page I am reading right now:  [http://ubuntuforums.org/showthread.php?t=949750](http://ubuntuforums.org/showthread.php?t=949750)  It seems to address the same issue but under an only similar problem. It also seems to tie into the instruction for using the "chmod" command I was given in post #2 of this thread. This seems to me to lend support to this

> chmod 644thing.

That is from post #2 in at that link.

Specifically the "644" permission it is speaking of. I will like to learn something more of ".ICEauthority" and "status 256" mentioned in those errors.

Thanks

---

### Post by ClientAlive on 2011-05-01
I have some additional information.

It appeared that a file named ".ICEauthority" was missing from my home directory (that home directory). I attempted to create the file inside the directory by running this command while in the directory.

```
 touch .ICEauthority 
```

The file was created but is blank. I then ran.

```
 chmod 644 /home/nane/.ICEauthority 
```

The terminal again complained that the file or directory did not exist.

I, once again, opened the file named "README.txt" which is a file inside that home directory - using

```
 less README.txt 
```

This is what it says:

```
 THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private 
```

Back to square one about mounting the directory. I have seriously struggled with doing this but I will try to go through the directions I had found last night on this.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#RecoveringYourDataManually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#RecoveringYourDataManually)

One difference is that, last night, I executed the instructions being logged in as root. I remember there was a reason for needing to do this but don't recall what it was. I think using "sudo" I was not being allowed to execute the commands.

---

### Post by CharlesA on 2011-05-01
Well you are making progress. I thought I saw a GUI way in the link above. Give that a shot.

You need to run them as root since a normal user can't mount and won't be able to install any programs if needed.

---

### Post by ClientAlive on 2011-05-01
> **CharlesA said:**
> Well you are making progress. I thought I saw a GUI way in the link above. Give that a shot.

You need to run them as root since a normal user can't mount and won't be able to install any programs if needed.


I did it brother! Glory to God - I did it!!! I got my personal data off of out of that home directory and copied onto my usb thumb drive. Once I got into the directory I had to hack the hell out of a couple things to get them out of there but I did it.

Now I just need to remove that home directory and figure out how to create a brand new home directory for that user (my regular account).

I'm pretty sure that to delete the directory I would run:

```
 rm -r /home/name 
```But I'm not sure how to create a new one.

Any ideas?

Thanks
--------------------------

Edit: The only challenge might come because I will have to do this from this other account: and then, I think I'll be back to having to manually point the user to it and set the ownership, etc. Just like what I'm dealing with now. If that is what I'm have to look forward to then I would be just as well off restoring the existing one - right? Unless what is mentioned in post #4 (at the end of that post)  [http://ubuntuforums.org/showthread.php?t=949750](http://ubuntuforums.org/showthread.php?t=949750)   gives me an option that may help. This guy claims he can log into that account that way. I'm not sure if it would help me or not to create the new home directory from within the account or hot? Would it allow me to avoid all kinds of drama with manually configuring things?

---

### Post by CharlesA on 2011-05-01
To create a new home directory, you would need to create it:

```
sudo mkdir /home/somefolder
```

Chown the directory:

```
sudo chown user:user /home/somefolder
```

And copy the files from /etc/skel/ to the new folder.

IMHO, if you got all your personal data off, it would be way easier to just reinstall from scratch and create the user you want during the install.

---

### Post by ClientAlive on 2011-05-02
Sorry I went mia for a day there. A long distance friend who's real good with these things offered to help. We worked on the thing for an accumulated 12+ hrs and nothing ended up working. Ultimately he talked me into going with Ubuntu 10.04 LTS and helped me get set up with all the little details to make my life a little easier working w/ Linux. I sure am glad to have friends like that.

CharlesA:

Thanks so much for keeping checking on me like you did. I sure appreciate you man. That really helped. I was pretty panicked that night; then, the next day when I woke up, I was a little more clear headed. That's when I finally got into that directory and got my personal data off.


> **bodhi.zazen said:**
> My advice is that you try these things in a virtual machine. You can break a virtual machine running in virtual box all you like without affecting you installation.

Once you get a feel for it, and have tested it out, then run the command on your main install =)


I have Oracle VM Virtual Box now and was given a crash course in using it. Now I can run things there first. Like you mentioned before bodhi. When you suggested that I didn't really know what that was and I wouldn't have known how to use it.


> **sisco311 said:**
> You can change a user's home directory with the usermod command: 
```
usermod -md /home/new user
```

For details check out its man page:
```
man usermod
```


Virtual Machine or no that wouldv'e been the better, safer way to do this. Wish I would have realized it when I made my choice.

Well I learned a lot. I learned not to screw with Linux. People have told me as much but I guess I had to see for myself.

---

### Post by CharlesA on 2011-05-03
Glad you got it working. :)

---

### Post by bodhi.zazen on 2011-05-03
> **ClientAlive said:**
> Well I learned a lot. I learned not to screw with Linux. People have told me as much but I guess I had to see for myself.

I would not say that =)

Keep one installation as your stable desktop and do not play with that.

Play all you like in a VM (Virtualbox), it is called learning.

Remember if you break Ubuntu you get to keep both pieces.

---

### Post by ClientAlive on 2011-05-03
> **bodhi.zazen said:**
> I would not say that =)

Keep one installation as your stable desktop and do not play with that.

Play all you like in a VM (Virtualbox), it is called learning.

Remember if you break Ubuntu you get to keep both pieces.

Yeah. After this debacle I figure it would be very wise even to practice my code in Virtual Box. I have a copy of the 10.04 iso in a folder ready to be set up in Virtual Box the next time I practice. (I'm running 10.04 now so it's a match). So this is especially good for a guy like me I think. I love to experiment around with code when I'm learning it. Take it to the next level you know.

Did you happen to see the thread where I tried to make 17 billion folders on my machine? I didn't know I was asking for that many until after the fact. Hmm . . . no wonder it froze up and the terminal window crashed on me. Lol.


> **bodhi.zazen said:**
> Remember if you break Ubuntu you get to keep both pieces.

Your makin' me laugh bodhi. Thanks man. I needed that.

Jake

---

### Post by CharlesA on 2011-05-03
Also, with VMs, you can take snapshots which rock. I have had ones where I totally borked the install, and saved it, then rolled it back to before the borkage.

---

