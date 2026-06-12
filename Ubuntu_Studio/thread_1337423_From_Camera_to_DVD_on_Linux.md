---
title: "From Camera to DVD on Linux"
date: 2009-11-25
forum: Ubuntu Studio
---

### Post by paulmerchant on 2009-11-25
I just made my first DVD on Linux and the process was easier than expected. I know many people are waiting for some of the killer Linux NLEs to become more advanced and stable, but there are already video editing work flows that can be used for just about any level of beginner or professional.

I followed a simple process:

dvgrab
  |
  V
Blender-->Audacity
  |
  V
DVD Styler

The command line dvgrab is outstanding. I ran it in interactive mode and it controlled the DV deck we have at work flawlessly. It even handles a special format that I shoot at home: 24p advanced. I can't wait to start editing some of my home footage.

Blender worked as expected for cutting up the clips. I guess this review is slightly unfair because I was already moderately familiar with the Blender interface. I did a short 3D project a few years ago. I had also tested the idea of using Blender as a video editor around that same time.

Audacity was needed because Blender didn't allow me to do much with my audio. Basically, after cutting my video, I rendered out my audio track and then loaded it into Audacity for some advanced editing and mixing. Then I brought this new audio back into Blender (and muted out all my old clips). For some reason, I had to slide my new audio over seven frames to bring everything back into sync, but it worked. This process couldn't be used on all projects, but as someone who spends way too much time tweaking things as I go, I found it refreshing to compartmentalize my audio work. For those who need more advanced audio capabilities, I have heard of people who successfully sync Blender with Ardour.

Finally, I looked at a couple of DVD authoring packages. The two I tried both looked fine (Devede and DVD Styler). I ended up using DVD Styler to build a menu and burn my DVD.

I guess I could complain about the lack of media management using this work flow, but Dolphin (I've been using KDE) or Nautilus can organize and preview media just fine.

I hope this little work flow helps or encourages someone. I know there are a dozen other ways to do the same thing. I just don't think people should let all the negativity surrounding video editing on Linux keep them from taking on a project.

---

### Post by ilil on 2009-11-26
Well, as for DVD authoring you can try my program, [Bombono DVD](http://www.bombono.org/). Any comments are welcome!

---

