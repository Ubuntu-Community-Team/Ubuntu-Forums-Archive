---
title: "AppArmor profile for lightdm-guest-session."
date: 2013-07-20
forum: Security
---

### Post by kleenex on 2013-07-20
Hi. Could someone explain to me why [COLOR=#008000]lightdm-guest-session[/COLOR] profile was changed? Some time ago, I checked this profile and there was a lot more entries. Now it's look like (I reinstalled **apparmor-profiles** package):

```
[COLOR=#000080]# vim:syntax=apparmor
# Profile for restricting lightdm guest session  

#include <tunables/global>  

/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper {  
 # Most applications are confined via the main abstraction  
#include <abstractions/lightdm>    

# chromium-browser needs special confinement due to its
sandboxing #include <abstractions/lightdm_chromium-browser>
}[/COLOR]
```

[COLOR=#008000]apparmor_status[/COLOR] command shows that there is two profiles in enforced mode, which are leated to lightdm:

```
[COLOR=#000080]/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper
/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser[/COLOR]
```

Why it happened. I may be wrong, but I remeber that this profile was full of policy, restrictions and looked completely different etc. One more thing: I'm not using a Chromium browser. Could somebody help me with this issue? For example paste full [COLOR=#008000]lightdm-guest-session[/COLOR] profile? Please.

Best regards!

---

