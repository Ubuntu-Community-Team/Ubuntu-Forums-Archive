---
title: "ubuntu server ACPI difficulties"
date: 2011-07-01
forum: Server Platforms
---

### Post by noobatron on 2011-07-01
Hi guys,

this question is such a combination of things i thought it'd be best to just post in the server section.

(the laptop referred to below is an LG E300, intel core 2 duo, running ubuntu server 10.04 x64 (clean install) with not much other than boinc installed and a few tools)

I have an old laptop which i have started using purely for BOINC, however, I am subject to rolling blackouts (joys of "developing" countries) and need this system to be able to suspend in order to get through a 3 hour blackout each day and come back up when a wake on lan signal is sent from my router with tomato firmware 

other than the two issues below, this has all been configured and tested to work manually and separately, but the whole deal doesn't come together.

by default, ethtool sets the laptop's wake on lan as found in [this]("http://www.tjansson.dk/?p=83") tutorial, this successfully puts the laptop to sleep when i call and is waken by wake on lan:
```
sudo /etc/acpi/sleep.sh
```i now have two issues to deal with:

1) wake on lan doesn't work when /etc/acpi/sleep.sh is called within my modified (but does when it's done manually!) "/etc/power/power.sh" script (i think there's some conflict or permission issue but nothing's been seen by me), this is obvious due to the fact that both WOL doesn't work and that the network link light turns off on the router this laptop is connected to.

the script as i've changed it is below, the part i've modified/added is in bold)
/etc/power/power.sh:
```
#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/policy-funcs

if [ -z "$*" ] && ( [ `CheckPolicy` = 0 ] || CheckUPowerPolicy ); then
    exit;
fi

[B]grep -q off-line /proc/acpi/ac_adapter/*/state
if [ $? = 0 ] ; then
    ethtool -s eth0 wol g
    /etc/acpi/sleep.sh
    exit;
fi[/B]

pm-powersave $*
```the reason i changed power.sh is because for some reason, when an AC adapter withdrawal event occurs, acpi script in the /etc/acpi/events/battery calls power.sh and it seems to work like this except for the above problem.

2nd problem is that while on standby, if the router is disconnected and reconnected from the laptop (in any case/situation whether due to an actual power outage or due to me experimenting), the laptop drops the connection (i assume to save power) and can no longer respond to WOL signals, even when i do this "successfully" when i manually call the suspend. i need to remove this feature to ensure that the laptop reconnects to the router when power/link is restored. I assume this can be done because i have another laptop (i have people's spares lying around) that can do this with standard ubuntu (not server) which i plan to later convert to server if this goes well.

just to clear up any confusion - this computer must hit standby mode when the power is cut/AC adapter is disconnected and restore on wake on lan signal after it's network link has been severed and restored. if there's a solution involving hibernate or shutdown and still being able to do this, i'm listening.

i thank anybody who has a solution in advance and will be more than happy to help with any queries, i have searched far and wide for solutions and have solved about 8 hurdles before being stuck here so a simple search won't do it anymore

UPDATE: changing any mention of /etc/acpi/sleep.sh with pm-suspend does the exact same thing, i guess they're essentially identical.

---

