---
title: "Church Sermon Recording"
date: 2018-04-18
forum: Ubuntu Application Development
---

### Post by joel3419813 on 2018-04-18
Hello,

I am a bit new to much of what I am working with so please forgive if I say something a shade off. I am working on creating something I thought was going to be simple.... The more I learn, the more I learn how little I know. I was asked for a way to record the sermons during the church service. This church has very very little in the way of electronics. The entire sound system is nothing more than a basic board to control volume and which mic feeds the speakers. So I figured a basic approach would be to feed from a headphone jack into a mic port and use arecord to save the output. I made a very basic menu window for them with python and Gtk. I would like to provide a way for them to be able to enter a title, hit record, and then be able to make CDs for anyone who wants one. No one at the building that will be using the system is familiar with anything computer related, so with this in mind I am trying to make it as simple as humanly possible for them. To be honest with everyone, I think I am going beyond what I would normally because when I was getting married they offered their building to me for nothing.

---

### Post by spjackson on 2018-04-19
Welcome to the forums.

I have found that non-tech users are able to record quite adequately using Audacity with minimal training. I would also suggest using a commonly used gui application for burning the CD (e.g. Brasero, Xfburn).

While building your own interface to arecord and wodim is possible, you will end up with a lot of work if you want to provide decent feedback to your users (progress, write-failure etc.)

---

### Post by joel3419813 on 2018-04-19
You may be right, it does seem like it will be a good amount of work. I think I found a method that will not need the use of arecord. I guess right within python you can accomplish the recording portion. [https://gist.github.com/mabdrabo/8678538](https://gist.github.com/mabdrabo/8678538)

---

### Post by Frogs Hair on 2018-04-19
Audacity is pretty simple to provide point and click instructions for and you can check and set microphone input  levels before starting. If cds are used keep about a 70 minute length in mind.

Edit: Audacity is also cross platform.

---

