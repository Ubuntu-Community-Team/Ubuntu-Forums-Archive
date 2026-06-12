---
title: "Firefox should save files readonly when invoking external apps"
date: 2007-12-03
forum: Ubuntu Brainstorm
---

### Post by loa on 2007-12-03
I think that Firefox should save files readonly to /tmp when I click on files that require apps external to Firefox.

Here is my story behind this problem (much abbreviated version):

I was sitting at gmail, and reading a mail with an attachment. I clicked that attachment, to open it in openoffice. I made a lot of changes, and after that I saved. Then I rebooted my computer, started openoffice and tried to open the file (from the file->recently documents menu). And BANG, error message "file does not exist".

So, the problem was that I forgot that I had opened it from Firefox. I should have taken Save as instead. And Firefox first saves the file to /tmp, and then invokes Openoffice (or whatever program it is) to open the file. And as I use shmfs for /tmp, everything of course got erased from there 

My fix for this problem is that Firefox should save these files in read-only mode to /tmp. Then when stupid users (like me) tries to save them, they will get an error message. Maybe not everyone would figure out what to do then, but I think it would many. My wife also made this once, and being quiet angry she said "Why are you able to save, if it is of no use?". And I think she is quite right.

This fix would probably be quite easy to implement, I think. And I suppose that I'm not the only one which has done this kind of mistake, it would probably be of benefit to a lot of people. And I can't really see any big downsides with this behavior.

What do you think about it? Maybe I've missed something important here, then you may please tell me about that.

/Regards

---

### Post by timcredible on 2007-12-03
won't matter, file will still still get erased from /tmp when you reboot.  /tmp is just that, temporary space, the real solution is to not save files there.

---

### Post by smartboyathome on 2007-12-03
The problem of deleting files in that would be troublesome (since read-only can only be read, not written or deleted). Stuff in there is deleted approx. every 6 hrs.

---

### Post by loa on 2007-12-03
Ok, my point was this. If the file is saved read-only, I will get an error message when I try to save it, and that will remind me of that I have to save it somewhere else. 

Computer newbies will probably get confused by this error message, but it would be a lot more informative for them to get such an error message instead of thinking that everything works, and get strongly confused later on when they can't find their file.

smartboyathome: is there some daemon cleaning /tmp regularly? but probably that daemon has super-user privileges, and will be able to remove the users files if necessary? Or have I understood things wrong?

Thanks for your comments

---

### Post by smartboyathome on 2007-12-03
I don't know if there is a daemon, but I do know that when I am on my computer, open something, then 6-12 hrs. later try to open it again, I get an error message saying that it has been deleted.

A daemon operating as a superuser instead of a normal user would be in my mind a security flaw more than it would be beneficial (it can delete any part of your file system if it goes on the frits and becomes corrupt). So I don't think that we want to go that route for this.

---

### Post by loa on 2007-12-04
Yes, I think you are right when you say that it would be a serious security flaw with a deletion daemon running as root. But this won't be an issue, as firefox removes all those files it downloads to /tmp when you close firefox.

Anyway, if there is such a daemon which automatically deletes files from /tmp, it must have some kind of privileges. If I take a quick look at /tmp, all files I see are only writable by the owner (that is me, or root). If I copy some file there, it will also be writable only by myself.
Is it not so that /tmp is wiped at bootup, and not continuously? At least this used to be the behavior earlier, IIRC.

The files Mozilla put there are also, as the situation is now, writable only for myself, and with my suggestion the only difference would be that the 'w' flag should be cleared even for myself. So another user without privileges (an unprivileged daemon for instance) is still unable to remove the files, and a user with sufficient privileges will be able to remove regardless.

But if there is still a problem with this change, then please tell me. If I would like to forward this to the developers in some way, what is the best way? Is it to file a wishlist bug in launchpad? Can anyone of you with more knowledge enlighten me about this?

---

### Post by loa on 2007-12-04
Oh, I forgot, and when Firefox then closes, it would probably have to change the file to be writable for the owner before it can delete it.

---

### Post by coolen on 2007-12-04
The whole point of the tmp folder is that it's for temporary files. The user who created them can modify or delete them, it's wiped regularly, etc. I don't know what mechanism controls the wipe, but there you have it.

This is a good idea, but it doesn't agree with the idea of the tmp folder. Perhaps it's possible to reconfigure Firefox to save to a different location, but this behaviour makes no sense if you're using tmp.

Personally, I'd use it.

---

### Post by Xbehave on 2007-12-04
afaik theres no mechanism to delete /tmp and by default when FF downloads a file it doesnt do anything to it, even if you close firefox it wont delte it (BY DEFAULT)

---

### Post by loa on 2007-12-04
Hmm, maybe I have to clarify again my intentions. I think it's perfectly good for firefox to save files in /tmp, that is what this directory is for. My important point is that the user should in some way get a note that he is doing something stupid when he tries to save that file.

To get a really helpful message, we would have to modify openoffice (and every other application), and make the browser open them with some special flag (telling the apps that it is a temporary file). Then the apps could put out some error message like "Warning: you are saving this file to temporary space. Probably you will not be able to open this file in the future, and then all your changes will be lost. Save the file in a different location instead, using File -> Save as." But modifying all other programs is certainly not feasible IMO.

If the the file is read-only, it would provide at least some error message to the user. The quick and easy way would be to to make Firefox (and other browsers) save the file read-only to /tmp. This would at least remind me, would I forget this thing again in the future.

And I am fully aware of that files will get away from /tmp regardless of if they are saved read-only or not. And that the user must save his file somewhere else. But this could help the user a bit.

---

