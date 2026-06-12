---
title: "License issue"
date: 2008-08-07
forum: The Cafe
---

### Post by kineem on 2008-08-07
Hello. I have used GPL licensed library in my software. But I written extra code to connect to my server. To prevent other users connect to my server without permission, I thought it would be more logical to license server code LGPL. 

So, first can I combine GPL and LGPL?

Second, I have read somewhere that all programs which use a GPL licensed code part, turns into GPL. If I combine LGPL and GPL , does all programs convert to GPL.  If all program turns into GPL then anyone can use my LPGL code that is used to connect to my server. And I cant prevent them connecting  and abusing my system. 

I just want to make sure that my server isnt used by others without my permission. I dont intent to restrict code distribution and share. What can I do?

---

### Post by saulgoode on 2008-08-07
> **kineem said:**
> So, first can I combine GPL and LGPL?
Yes. 

> **kineem said:**
> Second, I have read somewhere that all programs which use a GPL licensed code part, turns into GPL. If I combine LGPL and GPL , does all programs convert to GPL.  
If you integrate your own code with GPL code ***and distribute the result***, your code must be GPLed. If you don't distribute your code (in binary or source form) then you do not need to license it under the GPL.
> **kineem said:**
> If all program turns into GPL then anyone can use my LPGL code that is used to connect to my server. And I cant prevent them connecting  and abusing my system. 
I am confused by your statement. GPL won't prevent people from connecting to or abusing your system; it can only prevent products from being *distributed* under non-GPL licensing. The LGPL, for example, would permit someone to include your code (link to it, anyway) in a proprietary program which abuses your system, while the GPL would not. But releasing your code under either GPL or LGPL will not prevent anyone from *using* your code to abuse your system. 

> **kineem said:**
> I just want to make sure that my server isnt used by others without my permission. I dont intent to restrict code distribution and share. What can I do?
Well, you a not obligated to share your modified server code, even if the unmodified code is GPL/LGPL. If you do decide to share your code, you should not rely on its licensing terms to protect your server from unauthorized access or abuse; that is a separate issue.

You might receive some better advice if you were a bit more specific about what you wish to do.

---

### Post by az on 2008-08-07
But why do you think it's logical to release your code under the LGPL?

---

### Post by kineem on 2008-08-07
Of course the one that wants to abuse my server can do it without using her code, but then I can take legal precautions. If I GPL license my server code, then anyone would use my server resource. And I cant prevent them using my server even with legal precautions, right? I dont have much resources and  just  want to use the server myself. So I thought I should license the server code as LGPL for permissions.

---

### Post by original_jamingrit on 2008-08-07
As long as you're using a secure method of connection such as ssh or secure ftp, this should be a problem.  Although, I guess that depends on what type of server it is.

Software licenses **do not** affect people accessing the system, they just affect distribution and installation unless they explicitly say otherwise.  If you want a legal safegaurd against people talking about your server, you could present them with something along the lines of "Without my verbal or written permission, you are using this server without permission, and no permission is granted to view/download accessible contents, and the owner of this server holds no responsibility for any such viewing or downloading."  That should be enough for most cases in court, if you use it as a Message Of The Day or something on the index page, depending on whatever kind of server it is.

The law is often peripheral to the Internet world, especially when something happens internationally.  It might be better to focus on hard security rather than legal security.

---

