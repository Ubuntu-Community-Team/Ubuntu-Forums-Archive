---
title: "Steps to enhance privacy/security in 13.10"
date: 2013-10-08
forum: Security
---

### Post by P8DmbeW on 2013-10-08
I'm unimpressed with all the resources Canonical has put into developing things like the Smart Scopes. You'd think Privacy/Security would be more prominent in Canonical's priorities what with the NSA revelations. I'd move to something like Arch if I could but I don't have anywhere near the tech skill to do it. So I have to rely on distro's like Ubuntu and compensate for the poor privacy/security decisions of Canonical.

Lots of people are coming to Linux from Mac and Windows to get away from crap like Smart Scopes and Ubuntu still continues to implement. It's disappointing. I'll be uninstalling the whole Smart Scopes thing. But I'm interested in other steps I can take to enhance the privacy/security of Ubuntu 13.10. I'm concerned with Canonical's lack of attention to Privacy/Security and hope other Ubuntu users who value Privacy/Security as much as I do can share their knowledge to help me make Ubuntu more privacy friendly.

Thanks.

The first thing to cover I guess should be how to uninstall the SMart Scopes. I assume a Synaptic search for unity-scopes will allow me to delete everything except for Files and Applications? (Is there a quicker way to just delete all smart scopes?) I'm just interested in being able to search for files and apps on my own machine. Anything that is 3rd party or not on my machine, I don't want search occuring for. Disabling is one thing, uninstalling is safer and more secure so I'd like to uninstall.

---

### Post by Amorphous Serendipity on 2013-10-08
Hi P8DmbeW,

If you are worried about privacy in regards to the  features built into unity, I would suggest going with distro that has a  different default desktop environment.


[LIST]
[*]Try XUbuntu (light weight, easy customization, nothing with the word scopes in it)
[*]Do an encrypted install (32 character password)
[*]Setup UFW for easy firewall management
[*]Configure AppArmor settings
[*]Use Firefox (AdBlock Plus, Ghostry, Google Disconnect, No Script, Masking Agent [to edit browsers user-agent])
[*]Setup proxy chaining with ProxyChains (need to know the proxy)
[/LIST]

I could keep going, but I think that's a good start for now.

---

