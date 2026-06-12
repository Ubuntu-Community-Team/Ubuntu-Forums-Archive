---
title: "Parcelforce website - ONLY Internet Explorer"
date: 2011-12-08
forum: The Cafe
---

### Post by bazzer on 2011-12-08
So, the thread I replied to [here]("http://ubuntuforums.org/showthread.php?p=11520393#post11520393") was very old, and apparently old issues don't matter any more, even if they are still very much ongoing. I'm posting a new thread to bring it to people's attention.

I find it frankly astounding that Parcelforce's website has been written to specifically exclude anything other than Internet Explorer. They appear to have gone out of their way to prevent people using the site. Even if you spoof your user agent, the very, very poor code doesn't actually work.

I've emailed them - surprise, no response. I'll update when (if) they do respond.

---

### Post by haqking on 2011-12-08
> **bazzer said:**
> So, the thread I replied to [here]("http://ubuntuforums.org/showthread.php?p=11520393#post11520393") was very old, and apparently old issues don't matter any more, even if they are still very much ongoing. I'm posting a new thread to bring it to people's attention.

I find it frankly astounding that Parcelforce's website has been written to specifically exclude anything other than Internet Explorer. They appear to have gone out of their way to prevent people using the site. Even if you spoof your user agent, the very, very poor code doesn't actually work.

I've emailed them - surprise, no response. I'll update when (if) they do respond.

Works for me in chrome and chromium and firefox.

Which part exactly ?

---

### Post by bazzer on 2011-12-08
Ok, the specifics of it. 

The company I work for uses Parcelforce to book collections using their WDM online interface.[https://www.parcelforce.net]("https://www.parcelforce.net")

You have to log in to the system - and obviously I won't be able to let you have my login to test. 

However, you can quite plainly see their admission on the login page, down the bottom: You should install Internet Explorer (version 6.0 or better).... and so on.

---

### Post by Dry Lips on 2011-12-08
> **bazzer said:**
> Ok, the specifics of it. 

The company I work for uses Parcelforce to book collections using their WDM online interface.[https://www.parcelforce.net](https://www.parcelforce.net)

You have to log in to the system - and obviously I won't be able to let you have my login to test. 

However, you can quite plainly see their admission on the login page, down the bottom: You should install Internet Explorer (version 6.0 or better).... and so on.

Have you tried switching user agent? There's a firefox addon which does it for you. 
Or do they use silverlight or something?

---

### Post by bazzer on 2011-12-08
Switching user agent fools the browser check on the login page, but the method they use to populate drop down boxes in their "Collection Request" page is odd. Changing the value in the **Service** box makes the page reload - but crucially, the contents of the dropdown box dissapears at this point. So, when you click **Process**, the page complains you've not selected a service!

I have tested on a cr*p old windows box and IE6 somehow manages this. No idea how though.

---

