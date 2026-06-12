---
title: "can't rdesktop to Vbox on same machine as non-admin user"
date: 2015-01-21
forum: Virtualisation
---

### Post by EarlsFurniture on 2015-01-21
I'm presently running this setup:

'server' running an XP VM in Vbox in headless mode with VRDE on serving on port 5000. Vbox and the VM are running under my user which is in the admin group. (actually the original admin user)
'client' with non-admin user accessing the VM instance via rdesktop

This works fine.

The client machine is perfectly capable of running the VM directly. (at one time, it was a less capable box, hence the present setup)
After upgrading the box, I've successfully tested accessing a headless vm running in vbox via rdesktop. (that is rdesktop can display the VM running on the same physical machine as rdesktop)
The problem is that when I test with a non-admin user, rdesktop does nothing. It cannot display the VM.

I'm not sure if the problem is with rdesktop, or Vbox being run as a non-admin user.

I'm sure somewhere a permissions issue is the problem, but I'm not sure as to where. The solution cannot be to add the non-admin user to the admin group. There must be a way to allow non-admins to run a VM in headless mode (at startup) and then access it as needed via rdesktop. The only alternative I can think of is to have the VM start headless from an admin user somehow and then have the non-admin user access it with rdesktop. But I have no clue how to accomplish this as a startup item for non-admin users. (or any user, not the one actually logging in)

Why I want to do this:
I could just have the user start Vbox and then the VM normally, but there is only a single application they need to use. For the less computer savvy, it works better if they click an icon that matches their application on the launcher, and what they get is that app running in an rdesktop window. (I'll eventually set it up as single-application seemeless, but I don't mind letting them see the XP desktop for now)

Any assistance or wild guesses are greatly appreciated.

---

### Post by newbie-user on 2015-01-21
Did you add the non-admin user to the list of allowed RDP users in XP?

---

### Post by EarlsFurniture on 2015-02-14
Sorry for the delayed reply. I'm not getting notices via e-mail of replies from the forums and I haven't managed to get back here.

Thanks for the tip, but I'm not using XP's RDP. I'm using VBox's RDP server. I've turned it on via the vboxmanage VRDE ON command. (and setting it to on via the settings gui for some machines - same command I think)

I'll look for an RDP group on the linux side though to see if I can work out something there.

---

