---
title: "Streamtuner Patch"
date: 2005-05-17
forum: Ubuntu Backports
---

### Post by dlpfmVfH on 2005-05-17
The current release of streamtuner live365 plugin doesn't connect anymore to the live365 server,
because of a change at live365, there is a patch to correct the problem,

can you backport the new release of streamtuner live365 plugin with the patch??

from the developer:
I have released a patch fixing the problem
([http://savannah.nongnu.org/download/streamtuner/streamtuner-0.99.99-live365.diff)](http://savannah.nongnu.org/download/streamtuner/streamtuner-0.99.99-live365.diff)).

you can find the source here:
[http://savannah.nongnu.org/download/streamtuner/](http://savannah.nongnu.org/download/streamtuner/)

thanks

---

### Post by Technoviking on 2005-05-17
I will look at this late this afternoon or this evening.

---

### Post by dlpfmVfH on 2005-05-17
Thanks for looking in to this...

Hope you will be succesful,

I love the backport project !

---

### Post by Technoviking on 2005-05-17
Done, will show up in the backport mirrors over the next few hours.

Mike

---

### Post by dlpfmVfH on 2005-05-17
found the streamtuner package, and testing it now,
it seems it working again,

can download the live365 data, and get it working in beep-media-player!!

Thanks for the backport!

---

### Post by Xian on 2005-05-17
Thanks, Mike. Much appreciated.

---

### Post by psoleko on 2005-05-17
Very cool, always wondered why that didn't work in Streamtuner. Thanks Mike.

---

### Post by dlpfmVfH on 2005-05-18
still get some errors, when changing from live365 to shoutcast, 
when I run it in terminal it ends with a segmentation fault...

live365 works..though...

---

### Post by rwabel on 2005-05-18
works fine for me, thanks!

---

### Post by Technoviking on 2005-05-18
[QUOTE=aboe]still get some errors, when changing from live365 to shoutcast, 
when I run it in terminal it ends with a segmentation fault...

live365 works..though...[/QUOTE]
I'm not getting that. Shoutcast was down yesterday for a few hours, does it work ok today?

Mike

---

### Post by rwabel on 2005-05-18
[QUOTE=Mike Basinger]I'm not getting that. Shoutcast was down yesterday for a few hours, does it work ok today?

Mike[/QUOTE]
 for me both are working fine

---

### Post by dlpfmVfH on 2005-05-18
I think I just hit the downserver and it couldn't handle the change while it was trying to download from one server to the next

---

### Post by Majlo on 2005-05-18
For me Streamtuner + Patch worked fine :-) .Thx for backport

---

### Post by FreeEagle on 2005-05-18
hi there....


how can i get the backport..... ??? 

what should i do to get it ? 


Best Regards,
 FreeEagle

---

### Post by harryc on 2005-05-18
[QUOTE=FreeEagle]hi there....


how can i get the backport..... ??? 

what should i do to get it ? 


Best Regards,
 FreeEagle[/QUOTE][http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by everettattebury on 2005-05-19
I'm using Ubuntu on an imac.  Any chance of a PowerPC package for this?  Or will I have to learn how to compile it myself?

---

### Post by Technoviking on 2005-05-19
[QUOTE=everettattebury]I'm using Ubuntu on an imac.  Any chance of a PowerPC package for this?  Or will I have to learn how to compile it myself?[/QUOTE]
I just got a G4 at home, but have not gotten a chance to put Ubuntu on it. I hope to get that going soon.

Mike

---

### Post by FreeEagle on 2005-05-22
[QUOTE=harryc][http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)[/QUOTE]


thanks alot....


FreeEagle

---

### Post by harryc on 2005-05-22
[QUOTE=Mike Basinger]I just got a G4 at home, but have not gotten a chance to put Ubuntu on it. I hope to get that going soon.

Mike[/QUOTE]Mike, I have a G4 as well. Am looking forward to some great packages from Ubunto backports for ppc. Thanks for your time.

---

