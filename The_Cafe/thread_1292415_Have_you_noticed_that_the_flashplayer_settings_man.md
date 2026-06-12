---
title: "Have you noticed that the flashplayer settings manager is a fraud?"
date: 2009-10-15
forum: The Cafe
---

### Post by ikisham on 2009-10-15
Adobe's flash is now the most powerful tracking tool out there (besides viruses of course). Here's an important post about it [http://msmvps.com/blogs/hostsnews/archive/2009/09/16/1724116.aspx](http://msmvps.com/blogs/hostsnews/archive/2009/09/16/1724116.aspx)

But they pose as nice guys with their Settings Manager where we should be able to block their cookies. Only should...
I was suspicious before, that my settings were not making much effect but today I just checked at Youtube. I deleted all objects, set the manager to not allow to store any info and to 'not ask again', went to YT then went back to the Settings Manager and it was reset to allow 10KB (that's enough for their dirty work) and to 'allow storage of common flash objects'.
At the above blog post the guy suggests to make settings.sol (at ~/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys) read-only. I've made that and will watch if it works (he said that they install a substitute but then he made that read-only too).

Better get going with an open-source substitute soon.

---

### Post by Crunchy the Headcrab on 2009-10-15
Well what I think is obnoxious is that they don't include the settings manager in the plugin itself.  Why should I have to go to another site to use it?  Furthermore Adobe doesn't disclose what they collect.  That's comforting *rolls eyes*.  Anyway, I think Adobe are a bunch of crooks.  I use a lot of their products out of necessity, not because I like them.  I actually can't stand that company or their products.

---

### Post by Dr. C on 2009-10-15
Local Shared Objects or Flash Cookies are a little known method for advertisers to defeat regular cookie removal or incognito browsing and still track user browsing habits.
[http://www.theregister.co.uk/2009/08/19/flash_cookies/]("http://www.theregister.co.uk/2009/08/19/flash_cookies/")
[http://papers.ssrn.com/sol3/papers.cfm?abstract_id=1446862]("http://papers.ssrn.com/sol3/papers.cfm?abstract_id=1446862")
[http://en.wikipedia.org/wiki/Local_Shared_Object]("http://en.wikipedia.org/wiki/Local_Shared_Object") 
In Ubuntu they are located in a hidden directory /home/*<user>*/.macromedia/Flash_Player. A simple way to address this privacy issue is to empty this directory and make it read only.

---

