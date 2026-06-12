---
title: "Programatically read window title?"
date: 2022-06-04
forum: Ubuntu Application Development
---

### Post by pbnn on 2022-06-04
Greetings. I am attempting to port a C# application to Linux, one features of which was reading a title of a GUI window of another application. The only context I need to have it working is Ubuntu with its default configuration and default window manager. However, I am stuck as how to do it. I know it is possible, as applications such as xdotool can perform it with its "getwindowname" function with C code. As far as my knowledge goes, I need to rely on libraries managing X, such as Xlib or XCB, however as that is far from what I have experience with, I wanted to ask if someone could point me in the right direction on how to achieve that result. I attempted to translate [this]("https://stackoverflow.com/questions/8825661") code to C#, but ended up with the same issue as in the question.

---

