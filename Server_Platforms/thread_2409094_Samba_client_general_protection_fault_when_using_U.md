---
title: "Samba client general protection fault when using UID"
date: 2018-12-27
forum: Server Platforms
---

### Post by zorlax on 2018-12-27
Hello there,
 I hope I'm posting this in the right forum, if not hopefully some mod will have the grace to move it.

I'm having a weird issue with the samba client that I hope someone can shed some light on and that I can describe it properly,

When I mount a share specifying an UID, to get write access on the share, I can upload maybe one or two files before everything samba pretty much borks. The server is still happily serving files to other machines.
Using 'dmesg -w' too see what's going on I can see that there is a general protection fault somehow related to cifsd.

If I connect from a windows client there is no issue. If I skip the UID and instead sudo the files over there is no issue.

My client user has the same UID as the server user with write access but a different username. In my mind this shouldn't matter as the username is for accessing the share and the UID and GUI for controlling permissions once you have access.

Now, am I using UID wrong or could this be a bug?

Both client and server are running fully updated, as of posting, bionic.

---

### Post by QIII on 2018-12-27
Moved to ***Server Platforms*** for a better fit.

This does not appear to be a connectivity/networking issue but a client/server issue.

You are more likely to draw the attention of the right people in this sub-forum.

Cheers!

---

### Post by Morbius1 on 2018-12-27
How about adding the [COLOR=#0000cd]**nounix**[/COLOR] option to  your list of cifs mount options?

---

### Post by zorlax on 2018-12-27
> **Morbius1 said:**
> How about adding the [COLOR=#0000cd]**nounix**[/COLOR] option to  your list of cifs mount options?

If I don't specify the UID I don't get write access so I'm afraid it doesn't help me.

---

### Post by Morbius1 on 2018-12-27
I didn't understand your last post.

I'm not talking about replacing uid=xxx with nounix I'm suggesting adding nounix with uid=xxx.

---

### Post by zorlax on 2018-12-27
Right sorry, I'll try that. I tried "noperm" and that seems to work but I'll have to do more testing.

More testing done and I no longer think this is a samba issue, not completely anyway.

Using nounix, noperm or UID alone or with one another works fine IF I copy files using the command line. It is when I use the GUI (Gnomeshell Wayland) that everything goes south, but only a bit into the second file, I've chosen to test with three files.

Not sure how to proceed but thanks for the suggestions and feedback so far,

---

### Post by zorlax on 2019-02-09
I'll bump this since I've been unable to determine what is actually going wrong.

Would anyone here who runs Bionic on a NUC and be willing to test this too see if it works for them?

---

