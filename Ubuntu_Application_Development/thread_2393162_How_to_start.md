---
title: "How to start"
date: 2018-05-30
forum: Ubuntu Application Development
---

### Post by cloudplayz on 2018-05-30
Hello... this is like the second forum I have ever used so sorry... I would like to get into making applications for Ubuntu... I would like to know the best language to get into Ubuntu development... If it will help I am familiar in HTML, CSS, PHP, Python, JavaScript, Java (Android Development), and I am currently learning C#. I am unsure of what might be a viable option. From my research Python and C++ are the more common options. If at all possible could I use C# or Java since both in my opinion are similar.

---

### Post by TheFu on 2018-05-30
Welcome to the forums.

You can use any language you like. Depending on the sort of application(s), different languages will be "better" - for certain values of "better."

Qt is C++
GTK+ is C++
GTK is C
There are bindings for many other langauges for those toolkits.
There are other toolkits.

Ubuntu GUI interface apps used to have XML as a possible language to leverage all the GUI controls already included in 16.04 Unity.  [https://developer.ubuntu.com/](https://developer.ubuntu.com/) and [https://wiki.ubuntu.com/ubuntu-make](https://wiki.ubuntu.com/ubuntu-make)

Plus we all have different biases which help/hinder our choices.  C# and Java are possible, but Java will be slow, just like it is on every other platform.  Automatic garbage collection languages have left a bad taste for me. They never run at the right time, when expected.  OTOH, I learned to manually manage memory correctly, so memory management isn't scary.

I would suggest caution around using snaps, though canonical is pushing it hard. There have been many failed dependency issues for programs that use addons and plugins to extend functionality.  If your app is self-contained, a snap should be fine, but it will use more RAM and more storage than non-snap solutions.

There aren't many desktop app devs here.

---

### Post by david1222 on 2018-05-30
Good option is to make a small research online. There is a lot of good articles which compare different languages et. [https://www.netguru.co/blog/elixir-vs-ruby-which-one-is-the-language-for-your-next-project](https://www.netguru.co/blog/elixir-vs-ruby-which-one-is-the-language-for-your-next-project), say about pros and cons of each of them, show good and bad sides. Thanks to it you will find the best option for you and for what your goal is. :) Good luck!

---

