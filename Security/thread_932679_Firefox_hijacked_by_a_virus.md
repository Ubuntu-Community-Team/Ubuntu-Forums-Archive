---
title: "Firefox hijacked by a virus?"
date: 2008-09-28
forum: Security
---

### Post by grigio on 2008-09-28
I have Firefox installed in Hardy, everytime on start up it tries to connect to 321XXXXX... the XXXXX depends of the user (I tried to create a new one with no extensions)

I checked that string on about:config but I didn't find it. The start up page is (obviosly) about:blank
Any tip?

---

### Post by Amarsingh0793 on 2008-09-28
Go to edit > Options and check what your homepage is listed as. You can change it from there if needed.

---

### Post by grigio on 2008-09-28
did u read the message above?
```
The start up page is (obviosly) about:blank
```

---

### Post by cariboo on 2008-09-28
What is 

> 321XXXXX

Is it a username, an ip address, it would help if you were a little more forth coming with information.

Also are you saying that your startup page is about:config?

Jim

---

### Post by mc4100 on 2008-09-28
It's hard to know what you're referring to, so a screnshot would be really helpful. If you can **show** the problem, then take a screenshot via "Take Screenshot" (in Applications -> Accessories), and attach it to your post.

---

### Post by y-lee on 2008-09-28
Not sure but in Ubunu, go to System->Preferences->Preferred Applications and make sure that the default web browser is set to "firefox" and not "custom". I found that in a bug report btw.

---

### Post by mike1234 on 2008-09-28
It sounds like somehow you set you homepage to start as  blank. Clear all your cookies, cache, etc. Are you in Windows or Ubuntu? I never had anything like this happen in Linux. Windows yes.

M.

---

### Post by hansdown on 2008-09-28
Hi grigio.

I had the exact thing happening.
Whenever I started firefox, it would jump to "about blank", and say a download had not previously finished.

To fix this, I went to firefox edit> preferences> privacy. Under History I checked the box that says keep my history for...Set to 0 days. Also check the box that says erase history when firefox closes.This is just my preference.

Hope this helps.

---

### Post by grigio on 2008-09-29
321XXXXX is only a number, that it changes when Firefox starts.

I cleaned all personal datas, chronology, passwords, cookies.. but the issue persists.

---

### Post by grigio on 2008-09-29
I solved, the problem was Cairo Dock. I replaced the laucher command "firefox %u" with "firefox"

---

