---
title: "gui has just left the building those are its footprints right there"
date: 2011-09-17
forum: Security
---

### Post by josephmills on 2011-09-17
me and a friend where talking about this and I was wondering your thoughts. 
[http://theinvisiblethings.blogspot.com/2011/04/linux-security-circus-on-gui-isolation.html](http://theinvisiblethings.blogspot.com/2011/04/linux-security-circus-on-gui-isolation.html)

sorry if this is in the wrong sections did not know weather to put it in the CC or here in security :)

---

### Post by Dangertux on 2011-09-17
Well despite the fact that as always she presents herself as cocky and all knowing (usually ends up working out poorly for her). 

She does have some valid points. Though, this isn't anything really unknown. Honestly ITL has ridden the virtualization train into the ground. The game has changed since Blue Pill, and to be honest while ITL provides valuable data and research to the Hypervisor development community their research is very specific. It doesn't take into account a lot of factors that are present in the "real world" IE: not a lab environment.

While I've seen a couple of presentations made by ITL, and read quite a few of their papers in my personal opinion they aren't doing anything that hasn't been done. Breaking out of guest instances and hypervisor code execution is kind of an old hat. There are both newer and more reliable methods than what they are putting out right now and honestly, their cavalier attitude just makes them look childish.

So back on to the original topic, X11. They are absolutely correct that X11 is flawed in it's trust for other applications, as well as it's isolation of applications. My question. And what? If you have the type of access she is talking about in her article to a desktop system it's already game over. This is just another part of post-exploitation. Sure, it's one way to engineer a key-logger, or device foot printing application. 

As Joanna said in her comments "this isn't real research it's a Saturday morning blog post". I would agree with that, as generally speaking research that points out something people ALREADY know is well, trivial. That being said, it may also be a marketing tactic for Qubes.

Do I agree? Sure, of course I do. She's absolutely right. Do I think she's arrogant as all get out? Yep , I sure do. Do I think that sticking to system level security is the best way to go? Nope, not really, 5 1/2 years ago it was a great way to go, but there are so many other factors involved at this stage of the game it just feels like ITL is screaming "LOOK ME ME ME LOOK!"

Need an example : [http://www.invisiblethingslab.com/resources/2011/Software%20Attacks%20on%20Intel%20VT-d.pdf]("http://www.invisiblethingslab.com/resources/2011/Software%20Attacks%20on%20Intel%20VT-d.pdf")

Ok so what's new here? This was released May of this year and isn't much but a slight improvement over now industry standard escape methods utilizing the framebuffer. So they put a fancy spin on it and included Intel's VT-d technology , and utilize NIC's instead of the framebuffer to make the hypercall, to Dom0... It's creative, I will give them that, but not exactly earth shattering. 

My 2 cents , and a few bucks extra.

---

### Post by uncontrolable™ on 2011-09-17
I ran the commands she spoke of and here is what I see.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=202373&stc=1&d=1316286794[/IMG]

uncontrolable

---

### Post by Larkspur on 2011-09-17
I think you're running xinput test on the wrong device.  Use "xinput list" and use the other keyboard on that list.

---

