---
title: "Running a laptop with an external monitor"
date: 2011-11-28
forum: System76 Support
---

### Post by mgolden on 2011-11-28
I have seen several threads on this and other boards asking how to add an external monitor to Ubuntu laptop computer running an nVidia graphics card (such as featured in the Gazelle, Serval, and Bonobo).  I have written up a wiki page which clarifies the situation and should be of help to those who have purchased one of these machines.

[http://www.knowledge76.com/index.php/Using_An_External_Monitor_On_A_System76_Laptop_With_an_nVidia_Graphics_Card](http://www.knowledge76.com/index.php/Using_An_External_Monitor_On_A_System76_Laptop_With_an_nVidia_Graphics_Card)

Comments or improvements are of course welcome.

---

### Post by aranaea on 2011-11-28
I was just coming here to ask for help with exactly this.  I have a Serp7 and I've haven't been able to move off of 10.10 because I couldn't get the external monitors to work with the nVidia drivers on the 11.xx releases.  I just installed the nouveau drivers as described at the bottom of your wiki page and it's working great.  Much better than the nVidia drivers on 10.10 and now I can use the 'Displays' in settings instead of another tool altogether.  Thanks mgolden!

---

### Post by bill516 on 2011-11-28
Bravo mgolden.  Clearly written and it solves a real problem.

---

### Post by mgolden on 2011-11-29
I just added section titles to the article, and added some discussion about a screen resolution problem I had.  Will someone who is running Ubuntu (not Kubuntu, as I am doing) see if the problem applies to them as well?  aranaea, which are you running?

---

### Post by isantop on 2011-12-01
I should add that we recommend Twinview mode, which essentially stretches the X screen across both monitors. It has the added benefit of not disabling 3D Acceleration.

---

### Post by aranaea on 2011-12-02
> **mgolden said:**
> I just added section titles to the article, and added some discussion about a screen resolution problem I had.  Will someone who is running Ubuntu (not Kubuntu, as I am doing) see if the problem applies to them as well?  aranaea, which are you running?

I'm running Ubuntu with unity but I don't notice any issue with the screen resolution or font size.  I don't seem to have a "Application Appearance" tool in System Settings either, fwiw.

---

### Post by mgolden on 2011-12-02
> **isantop said:**
> I should add that we recommend Twinview mode, which essentially stretches the X screen across both monitors. It has the added benefit of not disabling 3D Acceleration.

I will try it again.  When I looked at it, under KDE at least, it seemed to have two screens that were not connected in any way.  You could open a window on one or the other, but not drag between them.

---

### Post by isantop on 2011-12-02
> **mgolden said:**
> I will try it again.  When I looked at it, under KDE at least, it seemed to have two screens that were not connected in any way.  You could open a window on one or the other, but not drag between them.

Are you sure it was twinview you were looking at? Make sure you're using the Nvidia configuration tool as well, as that could have some bearing.

---

### Post by mgolden on 2011-12-06
Maybe I wasn't looking at TwinView.  It's possible I had set it up as separate monitors.

I have modified the wiki page to reflect this discussion.

---

