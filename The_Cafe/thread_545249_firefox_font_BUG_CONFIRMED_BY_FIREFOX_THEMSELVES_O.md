---
title: "firefox font BUG CONFIRMED BY FIREFOX THEMSELVES ON IRC&lt; linux version 2.0.0.6 tested"
date: 2007-09-07
forum: The Cafe
---

### Post by nowshining on 2007-09-07
edit: SO FAR THIS ONLY AFFECTS THE MAIN BUILD FROM MOZILLA THEMSELVES - UBUNTU'S VERSION IS UNCONFIRMED...    
 
 
 
 
 
intel version has this problem - confirmed minutes before this post...
 
A certain .TTF (true type font) font can crash the firefox browser when set at the font size 10 and when this happens firefox will unexpectedly exit and there is not way but to either find the problem font by doing a test to test with each a new profile otherwise one will HAVE to create a new profile - this affects the users own firefox - all other users are unaffected..
 
links:
```
 
[http://talkback-public.mozilla.org/search/start.jsp?search=2&type=iid&id=TB35680274M](http://talkback-public.mozilla.org/search/start.jsp?search=2&type=iid&id=TB35680274M)
 
[https://bugzilla.mozilla.org/buglist.cgi?query_format=&short_desc_type=allwordssubstr&short_desc=nsFontMetricsXft::CacheFontMetrics&long_desc_type=substring&long_desc=&bug_file_loc_type=allwordssubstr&bug_file_loc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&keywords_type=allwords&keywords=&emailtype1=exact&email1=&emailtype2=exact&email2=&bugidtype=include&bug_id=&votes=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=d](https://bugzilla.mozilla.org/buglist.cgi?query_format=&short_desc_type=allwordssubstr&short_desc=nsFontMetricsXft::CacheFontMetrics&long_desc_type=substring&long_desc=&bug_file_loc_type=allwordssubstr&bug_file_loc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&keywords_type=allwords&keywords=&emailtype1=exact&email1=&emailtype2=exact&email2=&bugidtype=include&bug_id=&votes=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=d)

[https://bugzilla.mozilla.org/show_bug.cgi?id=279032](https://bugzilla.mozilla.org/show_bug.cgi?id=279032)



 
```
 
 
 
edit to test it urself download the ttf font below and in your home directory create if not already have a new folder in there .font the dot is there to make it hidden, copy the font inside that folder and restart firefox - go to the content tab of preferences and then go to advanced uncheck to allow pages to set their own fonts and so forth.
 
 
 
From there click okay..
 
 
 
Under Fonts & Colors  by default font set the size to 10 and find near the very bottom the font TOPIARY select it and within a second or two it should exit on u and when u try to start it up it will re-exit quickly or not show up at all, and when trying to run via terminal it will give you the error stated above in the links...and now remove it and ur profile should be back up and running or create a new one via terminal
 
 
 
firefox --profilemanager

---

### Post by aaaantoine on 2007-09-07
> **nowshining said:**
> edit: SO FAR THIS ONLY AFFECTS THE MAIN BUILD FROM MOZILLA THEMSELVES - UBUNTU'S VERSION IS UNCONFIRMED...    
 
 
 
 
 
intel version has this problem - confirmed minutes before this post...
 
A certain .TTF (true type font) font can crash the firefox browser when set at the font size 10 and when this happens firefox will unexpectedly exit and there is not way but to either find the problem font by doing a test to test with each a new profile otherwise one will HAVE to create a new profile - this affects the users own firefox - all other users are unaffected..
 
links:
```
 
[http://talkback-public.mozilla.org/search/start.jsp?search=2&type=iid&id=TB35680274M](http://talkback-public.mozilla.org/search/start.jsp?search=2&type=iid&id=TB35680274M)
 
[https://bugzilla.mozilla.org/buglist.cgi?query_format=&short_desc_type=allwordssubstr&short_desc=nsFontMetricsXft::CacheFontMetrics&long_desc_type=substring&long_desc=&bug_file_loc_type=allwordssubstr&bug_file_loc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&keywords_type=allwords&keywords=&emailtype1=exact&email1=&emailtype2=exact&email2=&bugidtype=include&bug_id=&votes=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=d](https://bugzilla.mozilla.org/buglist.cgi?query_format=&short_desc_type=allwordssubstr&short_desc=nsFontMetricsXft::CacheFontMetrics&long_desc_type=substring&long_desc=&bug_file_loc_type=allwordssubstr&bug_file_loc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&keywords_type=allwords&keywords=&emailtype1=exact&email1=&emailtype2=exact&email2=&bugidtype=include&bug_id=&votes=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=d)
 
```

I'm sorry, I lost you after "unexpectedly exit".

---

### Post by nowshining on 2007-09-07
that simply means it will  EXIT quickly and so quick that it will be gone in a poof.. :)

---

### Post by PetePete on 2007-09-07
so?
as long as it doesn't execute code with root priv im not that bothered.

---

### Post by nowshining on 2007-09-07
all i know it crashed my firefox :) but that's what i thought too... however i was letting the forums know and esp. the ubuntu team on their cruddy build of firefox i didn't like know of it on the forums and so they can test it on theirs and either confirm it crashes on theirs or somehow it was fixed in their twiddling with the code in the program... if you like ubuntus firefox then great - i hope they added an option to open up windows in a new tab tho, that's why i switched - the annoyance..

---

### Post by HarshReality on 2007-09-07
No offense thanks for the bug update but did you really need to do caps like that.... I mena yes, it closes and yes its a glitch but as pointed out above its not a security risk more of a bother. With Linux as it is if there was a post like thyis everytime a bug was found there would be no room for help on these forums.

Again, not saying its bad to report bugs and bring everybody up to speed you just have to prioritise. And in this case its a low priority...

---

### Post by nowshining on 2007-09-07
yes this is the CAFE where not helpful questions and answers get posted, if one needs help then they can go to the right help forum section..and I said BUG not Security risk... - i think everyone will know the diff. between a bug and a security issue..






edit: your telling me that other's posts are irrelevant here too sine they post non help topics here..

---

### Post by 23meg on 2007-09-07
> **nowshining said:**
> however i was letting the forums know and esp. the ubuntu team on their cruddy build of firefox i didn't like know of it on the forums and so they can test it on theirs and either confirm it crashes on theirs or somehow it was fixed in their twiddling with the code in the program... 

The way to do that is to file a bug. 

[https://bugs.launchpad.net/ubuntu/+source/firefox/+filebug](https://bugs.launchpad.net/ubuntu/+source/firefox/+filebug)

Forums are mostly frequented by users for support and discussion; development happens on Launchpad, IRC, mailing lists and the wiki.

---

### Post by nowshining on 2007-09-07
yes but i do not use ubuntus firefox , and with my current feisty with gutsy updates - i didn't do a full format just updates and no dist. update either, they will NOT accept any bug reports from ME.....

---

### Post by 23meg on 2007-09-07
Bug reports are accepted for all software in their supported and testing phases. If you modified your sources.list to point to the Gutsy repositories and followed all the updates, that's what you have: Gutsy, in its latest incomplete state. It's the development version, and if the bug is reproducible, it would be a valid one.

---

### Post by nowshining on 2007-09-07
well I do not have all yet, I certainly will NOT install firefox the ubuntu version, and I got that locked at my version, I do not have the latest open office, and I had to lock some updates incl. the dbus one as I did file a bug report, whereas it would freeze, go to the gutsy dev. forum and find a thread where I had the freeze and i got that answer from another user - prob. a dev. i don't know, well I understand that..... but To my extended knowledge I don't know to what extent i can be called a Gutsy tester, it says testing branch in the terminal outside of the gui and it says it in the system monitor, however like i said there are STILL Some updates that are not fully done, such as openoffice and firefox - if you know a way i can give it a shot or see if they will accept me - help me on that, :) i'll be with ya! but if not your FREE to report it of course...






edit: in other words some updates are locked for a REASON kapeesh!

---

### Post by nowshining on 2007-09-07
as for many libs and junk - yes i have the updates...

---

### Post by southernman on 2007-09-07
> **23meg said:**
> Bug reports are accepted for all software in their supported and testing phases. If you modified your sources.list to point to the Gutsy repositories and followed all the updates, that's what you have: Gutsy, in its latest incomplete state. It's the development version, and if the bug is reproducible, it would be a valid one.

nowshining, this is advice coming from someone who frequently interacts with the developers. [http://ubuntuforums.org/member.php?u=11472]("http://ubuntuforums.org/member.php?u=11472")

Just slow down, read and follow (if you so choose) their advice.

We know your just trying to be helpful... so ummm thanks!

---

### Post by nowshining on 2007-09-07
southernman i didn't check that out and thanks,  i don't really click on names to check them out lolz...but that was really helpful, but I again do not have ubuntus version of firefox so someone else with that version will have to test that out and create a bug report, I am again using Mozillas' version.. :) so I do not know the exact extent to which the ubuntu one was modified..so obstacle one is probably over but that last one is a bummer tho..

---

### Post by 23meg on 2007-09-07
OK, I'll see if I can reproduce the bug, and if positive, report it.

---

### Post by 23meg on 2007-09-07
I'm unable to reproduce it with Firefox 2.0.0.6 in Feisty.

---

### Post by tehkain on 2007-09-07
I am not able to reproduce the bug on my gutsy box with 2.0.0.6.

PS, you speak american well...

---

### Post by nowshining on 2007-09-08
maybe u guys didn't do it right, but if your using the ubuntu version then well i guess somehow it got fixed in their version or something.. and lolz on the american thing..

---

