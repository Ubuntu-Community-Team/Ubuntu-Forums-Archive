---
title: "Group management, or lack there of."
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Roasted on 2012-03-11
Today I was setting up a 12.04 box and playing around with some features. I began to tinker with it and ran into a snag. Previously, since Ubuntu/Linux has no sort of easy-to-use ACL feature where I can just add which user has access to which folder, I had to add my users to a group and assign that group to the folder if I wanted them to have access to.

Well, tonight I saw that the group part of the users and groups GUI was removed. Now, before you guys jump off the bridge and say oh just use terminal it's easy blah blah, that's not the point. Point is, we had GUI functionality that appears to have been taken away.

Why?

Moreso on top of the group question, why do we not have some sort of ACL for a folder? Why can I not right click on a folder and say Bob, Jim, Frank, you guys have access. Such a simple... solution... and it's not here. :( 

Because of the lack of an ACL, that's why I used the group. Not as glorified, but relatively easy. Add Bob Jim and Frank to group "public" or whatever, assign public to the folder, bam done! 

So, what do we do now? (besides resort to terminal, of course)

---

### Post by bmbaker on 2012-03-11
i don#t know why they removed it either! but you can re-install it with
```
sudo apt-get install gnome-system-tools
```

---

### Post by Roasted on 2012-03-11
> **bmbaker said:**
> i don#t know why they removed it either! but you can re-install it with
```
sudo apt-get install gnome-system-tools
```

I did see that, however it's kind of a LOL factor to see you have to install a depreciated tool in order to regain functionality that should already exist to begin with.

In a perfect world, we'd have the ability to simply add users to have access in some sort of ACL, but we don't.

In the previous world, we had the ability to easily manage groups in a GUI setting, and then thereby assign that group to the folder in question. Not glorified, but a semi decent work around.

In today's world, we have nothing.

Really?

---

### Post by cariboo on 2012-03-11
> **Roasted said:**
> I did see that, however it's kind of a LOL factor to see you have to install a depreciated tool in order to regain functionality that should already exist to begin with.

In a perfect world, we'd have the ability to simply add users to have access in some sort of ACL, but we don't.

In the previous world, we had the ability to easily manage groups in a GUI setting, and then thereby assign that group to the folder in question. Not glorified, but a semi decent work around.

In today's world, we have nothing.

Really?

The tool isn't depreciated, it's just that Gnome chose not to install it by default, and left it up to users that need it to install the tool.

The average user, which both Gnome-shell and Unity are aimed at usually don't have more than one user on their system, even if more that one person is using it, so what you are asking for is something a more advanced user would need.

Those of us that have been using. a Linux variant for some time, will have to get over the fact that one size fits all, we already get complaints about applets being installed that no one ever uses. unfortunately you can't please everyone.

---

### Post by Roasted on 2012-03-11
I understand you can't please everyone, but I just cannot really apply that mentality to this issue. I mean, groups... it's just a single radio button that already existed. It just makes no sense to me. Other things Ubuntu has done I've agreed with, removing Gimp from default CD because it was too advanced to begin with, etc. I get things like that, but I just can't agree with this.

I almost had to catch myself there with blaming Ubuntu, however I just realized that I was still running Unity on that box, so I guess the statement shall remain. :P 

From what I understood, that tool was depreciated, however it still worked. Is that true, or is that tool actually something that will be actively maintained into the future as the "advanced" user account management utility?

---

### Post by cariboo on 2012-03-11
> **Roasted said:**
> I understand you can't please everyone, but I just cannot really apply that mentality to this issue. I mean, groups... it's just a single radio button that already existed. It just makes no sense to me. Other things Ubuntu has done I've agreed with, removing Gimp from default CD because it was too advanced to begin with, etc. I get things like that, but I just can't agree with this.

I almost had to catch myself there with blaming Ubuntu, however I just realized that I was still running Unity on that box, so I guess the statement shall remain. :P 

From what I understood, that tool was depreciated, however it still worked. Is that true, or is that tool actually something that will be actively maintained into the future as the "advanced" user account management utility?

You'd have to check with the gnome developers to find out if the applet will continue to be maintained and updated.

---

### Post by Derek Karpinski on 2012-03-12
Just edit your fstab file to add acl functionality. Install package eiciel to get a GUI for acl settings.

But I agree with you about the old GUI for users and groups. We need it back.

---

### Post by Roasted on 2012-03-12
It's one thing to not have the feature yet. It's another to simply remove an easy to use feature that was already here.

---

