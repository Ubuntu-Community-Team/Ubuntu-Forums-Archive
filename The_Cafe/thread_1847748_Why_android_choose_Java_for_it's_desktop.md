---
title: "Why android choose Java for it's desktop?"
date: 2011-09-21
forum: The Cafe
---

### Post by papaapa on 2011-09-21
Hello!

Why do you think google choose java libaries for it's desktop environment. Android use as GPL-Linux but use java on it's desktop!? It was so difficult to write a new desktop environment or it would have problems with other libaries which are open source?

---

### Post by Beacon11 on 2011-09-21
First of all, do you know that you can write native C/C++ code for Android as long as any GUIs are in Java? Check out the NDK and Java JNI. There's also mono for Android if you like C#.

Second, there are a number of strengths to Java-- first, it runs in a VM which gives them control over how applications run and what they can access. It's also relatively platform-independent which doesn't tie manufacturers down. You honestly think it would have been better for Google to invent yet another language for people to learn just for Android development? Java exists and has a lively community. It makes good business sense to use a product that is already in use.

That said, would I have preferred to write Android applications in Ruby? Yes. Oh yes.

---

### Post by BrokenKingpin on 2011-09-21
They probably use the Java VM so if they ever had to switch to a different kernel/platform they wouldn't have to re-write the OS. Also, Java is an easy language to learn and develop with.

I do see your point though. I personally don't like Java, and it having the majority of the OS in java just slows everything down (although they have made some decent performance improvements in the last couple releases).

I liked the Maemo approach, which was more like a traditional DE, so it made it really easy to port desktop applications to the Phone. With Android you basically have to rewrite the application from scratch.

---

