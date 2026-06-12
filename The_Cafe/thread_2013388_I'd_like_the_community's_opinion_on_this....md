---
title: "I'd like the community's opinion on this..."
date: 2012-06-30
forum: The Cafe
---

### Post by isaacj87 on 2012-06-30
I'm currently managing the Unity-Revamped PPA. For the uninitiated, my PPA contains builds of Unity which revert the removal of the Dodge Windows behavior for the Unity launcher. It also contains Jonathan French's wonderful minimize/unminimize feature as well.

Since these are "custom" builds of Unity, I've been getting requests to include disabling the global menu from hiding. While I'm used to this behavior, I can understand how hiding the menus can irk some people.

So, my question is, how do you feel about the hiding menus? More importantly, given the way Unity handles the menus now, what would be the simplest solution to having the menus always visible?

Here's the main problem I'm running into: when a window is maximized, the title is displayed prominently in the *panel*. Obviously, since you guys already know this, when the user hovers over said title, the menu and window controls will appear. However, this is inconsistent with windows that are *unmaximized*. An unmaximized window contains the title and controls within its window and the menu is located in the panel!

Long story, short: If I want the menu to be displayed at all times, the title will always need to be cut off. Maximized windows will always need to have the title cut off because if I allow the user to hover over the panel to see the full title, then the menu goes away. Obviously, that can't happen. However, would having a cut off title be a usability problem for users?

I've already gone ahead and removed the hidden menus and I'm testing this right now. When maximized, the window controls appear when I hover over the panel; however, it kind of bothers me that I can't see the full title. I get the feeling I'm missing vital information.

Obviously, if I go ahead with this, non-hiding menus will be an option; however, I'd like to get the community thoughts on this...

---

### Post by madjr on 2012-06-30
hmm, I don't think you need to add any option to show menu by defaults, I thought that the devs are already working on providing this, so it should probably land for 12.10 ?


Also, if possible would be cool to see the **unity window quicklist**:

[http://www.webupd8.org/2012/06/unity-window-quicklists-switch-between.html](http://www.webupd8.org/2012/06/unity-window-quicklists-switch-between.html)


:guitar:

---

### Post by isaacj87 on 2012-06-30
> **madjr said:**
> hmm, I don't think you need to add any option to show menu by defaults, I thought that the devs are already working on providing this, so it should probably land for 12.10 ?


Also, if possible would be cool to see the **unity window quicklist**:

[http://www.webupd8.org/2012/06/unity-window-quicklists-switch-between.html](http://www.webupd8.org/2012/06/unity-window-quicklists-switch-between.html)


:guitar:

I've seen a bug report for non-hiding menus, but I haven't seen any concrete evidence that the Unity devs are working on this. I know someone has implemented this for Unity-2D, but that doesn't help us Unity-3D people. ;)

That would be great if this option is available in 12.10!

I looked the Unity window quicklists. It's a python script, but I'm sure it could implemented into Unity's code. Unfortunately, my time is limited, but I may look at it if I find time in the future. :)

---

### Post by rai4shu2 on 2012-06-30
FWIW, I think the menus belong in the window except when maxed. This is probably the best way to handle them.

---

### Post by houseworkshy on 2012-06-30
You could have both.   One way for unmaximised windows may be to have the title bar drop down, when hovered over, the top line and clickable objects on it being unchanged but with additional information showing in the drop down area below.  This info wouldn't show when the cursor wasn't over the bar so yes it would be abreviated but as the info is only a short mouse slide away it wouldn't matter.

---

### Post by Linuxratty on 2012-06-30
> 
So, my question is, how do you feel about the hiding menus? 

 I don't like them hidden,so I don't use Unity. I want to point and click and see menus.

---

### Post by isaacj87 on 2012-06-30
> **Linuxratty said:**
> I don't like them hidden,so I don't use Unity. I want to point and click and see menus.

If you were able to force the menus to be always visible, would you use Unity?

Thanks for the feedback, guys. Unfortunately, I'm not trying to "reinvent the wheel" here. I'm trying to stick as closely to the Unity-way of handling menus. This is mostly due to lack of time and skill required to make any major changes.

If it were my way, I would remove putting anything in the panel. The only thing I would put up there is the application name and menu bar (a la OS X).

---

### Post by madjr on 2012-07-02
> **isaacj87 said:**
> I've seen a bug report for non-hiding menus, but I haven't seen any concrete evidence that the Unity devs are working on this. I know someone has implemented this for Unity-2D, but that doesn't help us Unity-3D people. ;)

That would be great if this option is available in 12.10!

I looked the Unity window quicklists. It's a python script, but I'm sure it could implemented into Unity's code. Unfortunately, my time is limited, but I may look at it if I find time in the future. :)

yeah i havent seen any work yet, but is in this bug desc.

[https://bugs.launchpad.net/unity/+bug/682788](https://bugs.launchpad.net/unity/+bug/682788)


"[I]Desired change:

Implement the 'Enhanced Menu' project for 12.10. This project will address the issue described in this bug and also issues described in the duplicates of this bus. Note this is the 'official' bug that tracks the implementation of this project.

The following options will be added to 'System Settings/Appearance':

-------
Menus
Location: Global/Local
Visibility: Hidden/Always displayed
-------

More details to follow during the 12.10 cycle... ;-)[/I]"


so lets see how that goes.

anyway what you currently have looks good to me.

cheers !

---

