---
title: "why does this not exist"
date: 2009-09-23
forum: The Cafe
---

### Post by cmay on 2009-09-23
I was thinking of that when you have a debugger for bugs why can you not have a unborker for those who bork their systems.

. I am sure that many people could have a use for such invention and that if it was made userfriendly with a gui version and a cli version it would be a great tool that most people would love to have in their linux toolbox. 

what do you think.?

---

### Post by Warpnow on 2009-09-23
They call it a livecd.

---

### Post by Biochem on 2009-09-23
Isn't that called a backup?

---

### Post by mcduck on 2009-09-23
> **cmay said:**
> I was thinking of that when you have a debugger for bugs why can you not have a unborker for those who bork their systems.

. I am sure that many people could have a use for such invention and that if it was made userfriendly with a gui version and a cli version it would be a great tool that most people would love to have in their linux toolbox. 

what do you think.?

I think you have a bit strange idea about what a debugger is. :)

They are not programs that remove bugs. They only help developers to fix the bugs by telling information about what location in the program the crash happened, and reporting data from different variables at the time. It's still up to the developer to figure out what's wrong and how to fix it.

Based on that your "debunker" would pretty much be the log files. They tell you what's wrong so you can fix it.

(I'm sure there would be hundreds of thousands of very happy programmers if somebody actually invented a debugger that would fix the bugs for you.. :D)

---

### Post by cmay on 2009-09-23
I was just joking around with the play on the words 'debugger 'and "unborker "... I am aware that a debugger does not remove bugs in a magical fashion. :)

---

### Post by The Toxic Mite on 2009-09-23
> **cmay said:**
> I was thinking of that when you have a debugger for bugs why can you not have a unborker for those who bork their systems.
 
. I am sure that many people could have a use for such invention and that if it was made userfriendly with a gui version and a cli version it would be a great tool that most people would love to have in their linux toolbox. 
 
what do you think.?
 
That is **the STUPIDEST QUESTION **I have ever read... :|

---

### Post by cmay on 2009-09-24
Am I really the only one that thinks this was very funny :)

---

### Post by Sean Moran on 2009-09-24
> **cmay said:**
> Am I really the only one that thinks this was very funny :)

I almost got it, but before I could stop myself I took off into serious techie sort of thoughts and the humour escaped me, but it did rate a quick visual before I got sidetracked.

An "unborker" ?  I can think of a few possible solutions, but nothing all that user-friendly. :)

---

### Post by cmay on 2009-09-24
I think as a commandline app it is user friendly. as example this new command 
```
sudo unbork --ALL
```

---

### Post by ibuclaw on 2009-09-24
Union Filesystems are good for this... (requires patching/compiling kernel)

If you bork your system, just reboot and all changes are reverted back to what it was before you mounted the filesystem(s) over your main partitions.

I've been doing this alot with upgrading to Karmic without any persistent/physical upgrade happening. :)

Regards
Iain

---

### Post by MasterNetra on 2009-09-24
sudo rm bork

and its gone. :p

---

### Post by cmay on 2009-09-24
> **MasterNetra said:**
> sudo rm bork

and its gone. :p

This advise should be stickied....imagine all the time and troubles saved :)

---

### Post by Simian Man on 2009-09-24
alias unbork='rm -rf /'

---

### Post by cmay on 2009-09-24
I actually found a piece of code on googlecode search that uses an unborker. 
full source here.  
[http://code.google.com/p/gmail2-for-opera/source/browse/trunk/gmail2-for-opera/gmail_2.0.js?spec=svn2&r=2](http://code.google.com/p/gmail2-for-opera/source/browse/trunk/gmail2-for-opera/gmail_2.0.js?spec=svn2&r=2)    

code fragment here. 
```
               
      var cmFix = new Fix('_MD_Prepare("cm")');
                        cmFix.addUnborker(fixRichTextBrowserBlocking, fixRichTextFontSize);
                        
                        var eFix = new Fix('_MD_Prepare("e")');
                        eFix.addUnborker(fixGetSelectionParentElement, fixHilite, fixQuote);
                        
                        var evalFixes = new Fixes();
                        evalFixes.addFix(cmFix, eFix);
                        
      window.eval = function(str) {
        str = evalFixes.unbork(str);

```

so it seem like unborkers are invented already .....................

---

### Post by 3rdalbum on 2009-09-24
I was actually going to write a utility called "Seconds From Disaster" that keeps very detailed logs of the exact state of your computer at all times, so if you have a full kernel panic you can see what happened straight before.

---

