---
title: "On behalf of an other member"
date: 2009-07-17
forum: Resolution Centre
---

### Post by Closed_Port on 2009-07-17
Hi,

this is probably pretty unusual, but I stumbled over some posts by an other user and they think mods made several mistakes in handling these posts.

So I hope it is ok to bring this up here.

Yesterday the user mihaiv posted a topic about a security issue he thinks sudo has. He posted it, as far as I can tell, in the right forum.
The thread is here:
[http://ubuntuforums.org/showthread.php?t=1215058](http://ubuntuforums.org/showthread.php?t=1215058)

If I understand him correctly, he describes a possible method of privilege escalation, making it possible to get root access from a compromised non-root account.

The thread was quickly closed, as it seems by bodhi.zazen, who not only closed the account but also posted a very strong worded take down of what the original poster had written.

I do have have several issues with bodhi.zazen's actions.

1. He obviously misunderstood what the original poster had written. Contrary to what bodhi.zazen claimed, the vulnerability would not require to already have root access. At least, that's my understanding of the method described. 

2. I don't think it is appropriate for a moderator to harshly take down a forum member publicly and then to not give this forum member at least the possibility to answer publicly. I don't think that's the way we should treat each other here.

3. By closing the thread bodhi.zazen made it impossible to correct his misconceptions of what the poster had written or to at least clear it up if there was a misconception. 

I became aware of this thread when I found this post by the same user who started the original thread, this time in the community cafe:
[http://ubuntuforums.org/showthread.php?t=1215648](http://ubuntuforums.org/showthread.php?t=1215648)

This thread was also immediately closed. While I can see why it was closed, the poster was told by the moderator who closed it to use the appropriate forum for discussions about security, the very thing the post had originally done.

So, there you have it.
I think that the original thread should be reopened and that the user should be given better guidance on what to do.

---

### Post by KiwiNZ on 2009-07-17
I do not believe the Admin acted  harshly. I support the post he made and the closure of the thread.

The member does have the ability to respond if they so wish here in the Resolution Center.

---

### Post by Closed_Port on 2009-07-17
> **KiwiNZ said:**
> I do not believe the Admin acted  harshly.

Then we seem to have different definitions of harsh. Some examples:
> It is nothing but smoke and mirrors.
...
The whole discussion is a farse ...
...
"help the sky is falling"
...
full of partial or outright misinformation and lots of FUD

I don't know, I find that very harsh. 
> **KiwiNZ said:**
> 
I support the post he made and the closure of the thread.

But the post is factually incorrect. You don't see this as a problem?
> **KiwiNZ said:**
> 
The member does have the ability to respond if they so wish here in the Resolution Center.
I think that the member is not really sure about how to handle this situation. At least that's the impression I got from his thread in the community forum.

Maybe someone from the forum staff could contact him and explain the situation?

---

### Post by bodhi.zazen on 2009-07-17
I will respond with a long winded post.

The issue is IMO falls under either social engineering or escalation of privileges once the system has already been cracked.

The security threat here is not *.desktop (or .bashrc, or anything in $HOME or /).

The security thread is whatever allowed the user account to be compromised in the first place.

If it is via physical access, there are tons of things that can happen from key loggers (hardware and software) to modified kernels to replacing almost anything in /*

If is because a user account is compromised, again one can install almost anything in $HOME/.secret_directory or /tmp/.hidden and, as a user, edit most any file in $HOME to call such a malignant program, from .bashrc to *.desktop.

Once you have been compromised there are a thousand points of attack and with many cracks code is injected directly, no need to wait for the owner of the cracked account to do anything.

Again the security problem is not with .bashrc or *.desktop.

Most crackers inject code or install rootkits . No modern cracker would be so sloppy as to leave a *desktop file.

For example:

[http://www.mozilla.org/security/anno...sa2009-41.html]("http://www.mozilla.org/security/announce/2009/mfsa2009-41.html")

This crack injects (java) code directly to obtain a shell.

So my objection is that people talk about the problem as if it comes from *.desktop when really the problem comes from somewhere else.

If you think about it, if a cracker has shell access or a password to an account, it is not really possible to restrict what they do. There is no way to lock down .bashrc (or anything else in $HOME) from yourself. If nothing else, install a key logger or rootkit (crude but effective).

If you look at any rootkit they do not bother with $HOME, they go for hidden processes or hidden directories in /tmp . If the system is re-booted, /tmp is cleared, and it is hard to trace their tracks. a *.desktop (or anything visible to the owner of the cracked account) would be sloppy.

The only things which will possibly help are :

1. Do not install untrusted applications / code or run code you do not understand.

2. Restrict physical access.

3. Encryption.

4. Education re: social engineering.

5. Apparmor / SELinux.

So it is not that it can not happen, it is chasing one's tail to talk about the security risk of *.desktop as that is not the true security flaw in the first place, it is prevention of escalation of privileges at best.

Furthermore, if you read these threads, what happens next ? New users read and start posting "OMG, and I thought Ubuntu was secure" and "I hope someone fixes this" etc etc.

So the conversation degenerated very rapidly into nothing more then FUD and chicken little "The sky is falling".

People who start these threads then increase the drama claiming they are being suppressed or ignored or that they know more then the mods / staff who close the threads, etc, etc.

Which means these threads are nothing short of trolling and the result is un-necessary FUD in new users.

Non-trolling conversations go different. You educate the OP and they learn. No drama, just education. The topic turns from *.desktop or .bashrc to one of the 5 issues I posted and everyone benefits.

Last, the Ubuntu forums is not the place to post malignant code or "proof of concept".

With that the question is asked and answered. Let us turn the conversation to the true threats and decrease the FUD.

---

### Post by bodhi.zazen on 2009-07-17
I am going to close this thread now as again the question has been asked and answered and there is no need to continue on with the drama.

If another admin wants to re-open the thread I do not object.

If you wish to discuss the issue, use recurring discussions :

[http://ubuntuforums.org/showpost.php?p=7627901&postcount=4](http://ubuntuforums.org/showpost.php?p=7627901&postcount=4)

There are several threads still open listed in that post and if you take the time to read them you will see this topic is old and goes round and round.

If you wish to learn security start in the security section:

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

You will learn more about security spending an hour with this thread :

**[B]Sticky:**[/B] 			                          			 			[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")

Then you will ever learn from those recurring discussions.

---

### Post by bodhi.zazen on 2009-07-17
On second thought I will re-open this thread for comment so long as it stays on topic and does not degenerate into a recurring discussion or "proof of concept" for *.desktop or .bashrc or such.

If you turn this conversation into such a recurring discussion I will close it.

---

### Post by Closed_Port on 2009-07-17
After seeing in this thread how immature the admins of the forum react to criticism, it's time for me to say goodbye: [http://ubuntuforums.org/showthread.php?t=1215694](http://ubuntuforums.org/showthread.php?t=1215694)

Having posted a complaint in the Resolution Center, all I got was a chest thumping post from Kiwinz ignoring all the points I made and a very long and very uninformed post by bodhi.zazen. 

He seems to be blissfully unaware of the fact that privilege escalation is indeed a security problem and he seems to be totally ignorant of the fact that restricted privileges are at the very core of Linux security. This is outright scary coming from an admin of this forum.

To add insult to injury, he also doesn't deem it necessary to address the factually incorrect statements he made in his original post but instead again accuses the original poster of spreading FUD. Not because of what the poster said, but because of what bodhi.zazen knows would have happened in the future had he not heroically intervened, attacked the poster and closed the thread. Wow.

Of course he then immediately proceeds to close the thread, lest someone had the unfortunate idea to challenge his drivel.

Unfortunately, this kind of behavior by forum staff seems to be quite frequent. Just look at this little gem of cariboo907 spreading lies to deflect criticism of ubuntu. Needless to say, he never felt the need to correct himself:
[http://ubuntuforums.org/showpost.php?p=7605536&postcount=4](http://ubuntuforums.org/showpost.php?p=7605536&postcount=4)

And though I find it difficult to say this about people who obviously give their free time for these forums, the only conclusion I can draw from this is that many members of the forum staff are absolutely not capable of being staff on a forum of a huge free software project. 

The many people who spend their time on these forums helping others and Ubuntu as a whole deserve better.

To make a long story short, please delete, deactivate my account or whatever you do in cases like this.

---

### Post by bodhi.zazen on 2009-07-17
And with that I shall close this thread now.

---

### Post by matthew on 2009-07-17
See: [http://ubuntuforums.org/showthread.php?p=7632934#post7632934](http://ubuntuforums.org/showthread.php?p=7632934#post7632934)

---

