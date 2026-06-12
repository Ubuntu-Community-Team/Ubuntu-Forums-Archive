---
title: "alt-s in Firefox 2.0"
date: 2006-10-28
forum: The Cafe
---

### Post by meng on 2006-10-28
Yes, I've followed the herd and upgraded to Edgy (on my notebook computer, that is, I'm not ready to move my main system just yet) and overall I'm very impressed. BUT I am accustomed to using Firefox to browse and post in these forums, and I'm disappointed that alt-S is now a shortcut to the History menu, so I can't use it as a shortcut to submit a post in this forum.

Anyone else miss this? I have to reach over for the mouse to post now!

---

### Post by Steveire on 2006-10-28
In about:config set 
```

ui.key.contentAccess = 4

```

---

### Post by meng on 2006-10-28
Thanks

---

### Post by prizrak on 2006-10-28
Yes it also annoyed the hell out of me in FF2 (it's not an Ubuntu thing).

---

### Post by BarFly on 2006-10-28
I have a similar problem with alt-s.  I am used to using the command to enable Sage, my RSS reader.  I cannot imagine a situation that I would want a shortcut to the history.  However, I constantly want to look at my feeds.  Any ideas?  Maybe I should post this is Mozillazine instead of here.

---

### Post by meng on 2006-10-28
The solution is posted by Steveire. Works great.

---

### Post by BarFly on 2006-10-28
Good point, Meng.  I guess I was too distracted listening to football to actually read.  Thanks, Steveire!  Now to solve my tab problem...  Not to be posted here.

Geez, just yesterday I finally got FF 2.0 to actually not hang up.  The day before, I found out that my Edgy upgrade did not really take fully and found out how to fix it.  I knew there was a reason that I normally don't use software on the day it comes out...  I am happy with Edgy and FF 2.0, though.

---

### Post by Steveire on 2006-10-28
The other 'fix' I needed to apply to ff2.0 was to make typing '/' give me a more functional searchbar than the default. Open your userChrome.css for editing:
```

kate .mozilla/firefox/*/chrome/userChrome.css

```
(or gedit for gnomes) and add this:
```

/*
 * Fix the searchbar.
 */

#FindToolbar > * { display: -moz-box; }

```
Back to a useful tool.

---

