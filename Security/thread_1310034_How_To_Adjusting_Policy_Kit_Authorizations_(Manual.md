---
title: "How To: Adjusting Policy Kit Authorizations (Manually)"
date: 2009-11-01
forum: Security
---

### Post by pjomega on 2009-11-01
[SIZE="2"]So you've just upgraded to Karmic?
So you want to adjust your cpu scaling from your panel?
So you're getting really tired of typing your password every time you adjust it?[/SIZE]

You need to adjust the authorization policy setting for cpufreq. 

In Jaunty you'd go to **System/Administration/Authorizations**, but in karmic that's nowhere to be found. Evidently Authorizations is bundled with the old *policykit* framework, and karmic has moved on up to *policykit-1* (informative naming, i know...). If anyone has a gui for administering policies in *polkit-1* do post it, but so far as i know none exists (yet) for the new one. But don't despair. Policies are set on a per action basis defined as XML *.policy* files in /usr/share/polkit-1/actions/. To get a better idea how the system deals with action policies, check out the manpages for *polkit* and *pklocalauthority*.

_**[SIZE="2"]Example: Authorizing Cpu Scaling[/SIZE]**_

Check out the authorization window:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=134201[/IMG]

Notice the action is _org.gnome.cpufreqselector_ . 

Edit this policy in your favorite editor. For quick xml editing i like gedit:
    **gksu gedit /usr/share/polkit-1/actions/org.gnome.cpufreqselector.policy **

Look for the defaults element.

[INDENT]<defaults>
[INDENT]<_allow_inactive_>**no**</allow_inactive>
<_allow_active_>**auth_admin_keep**</_allow_active_>[/INDENT]
</defaults>[/INDENT]

You have three keys to choose from:
[INDENT]_allow_any_  -> authorizations for any client (active and inactive)[/INDENT]
[INDENT]_allow_active_  -> authorizations for clients in the active session[/INDENT]
[INDENT]_allow_inactive_   -> authorizations for clients in inactive sessions[/INDENT]

I'm not sure how these are prioritized, but realistically you only need either the first one or the second two. Cpufreq defines the second two by default.

These keys can take a number of values:
[INDENT]**no**   -> don't allow the action[/INDENT]
[INDENT]**yes**   -> allow the action implicitly[/INDENT]
[INDENT]**auth_self**   -> require the current user to authenticate the action[/INDENT]
[INDENT]**auth_admin **  -> require an admin user to authenticate the action[/INDENT]
[INDENT]**auth_self_keep**   -> require the current user to authenticate the action but retain authorization for a little while[/INDENT]
[INDENT]**auth_admin_keep**   -> require an admin user to authenticate but retain authorization for a little while [/INDENT]

By default, cpufreq denies any attempt by an inactive session to alter the scaling and requires an administrator password to change it on an active session. It also retains the authorization for some minutes after it's given. On a multi-user system, requiring an admin to throttle the cpu is probably a wise policy, but for a desktop system, or particularly a laptop, this becomes annoying. I'm going to deny access to inactive session clients and implicitly authorize active session clients (me).

[INDENT]<defaults>
[INDENT]<_allow_inactive_>**no**</_allow_inactive_>
<_allow_active_>**yes**</_allow_active_>[/INDENT]
</defaults>[/INDENT]

Save the policy, and it will take effect immediately.

---

### Post by riseringseeker on 2009-11-16
Thanks for this.  It's crazy how this is implemented, I think it's another example pointing to the fact that this release feels a little rushed in some areas.

I was looking for a way to change the timezone for a single user.  I change timezones quite frequently, and wanted to be able to change them without having to enter my password every time.

It appears the above does this, but it changes the displayed timezone for every user, not just the one who made the change.  It's not a big deal on my laptop, as I am the only one that uses it 99% of the time.

That said, I would like to have the ability for myself and my wife to display whichever timezone we want, and have it be different for each of us if that is what we choose.  I also do NOT want the kids to be able to do so (i.e. only admins, not desktop users).  I don't suppose you know of a way to do this?

---

### Post by Felliph3 on 2009-11-24
OMG Thanks so much!!! This was pissing the hell off, and most times it wouldnt allow the speeds to be changed even with the right pass! Good stuff.

---

