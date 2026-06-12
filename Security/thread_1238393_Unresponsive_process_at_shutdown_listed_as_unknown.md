---
title: "Unresponsive process at shutdown listed as unknown"
date: 2009-08-12
forum: Security
---

### Post by risingsun on 2009-08-12
Hi, seems a simple description but I'm not sure what the underlying cause was, it just alerted me at an attempted shutdown. However the fact it was non-responsive (and alerted me) is not what bothered me, moreso that Ubuntu just told me it was "Unknown". I ran ps x and I couldn't see anything new listed. 

Was this something inocuous such as a one off faulty process or something more sinister? And is there anything I should check for (I saved the process list at the time since I don't like the notion of 'unknown' as a process name.) It doesn't seemed to have occured again yet.

Many thanks.

Edit: Additional, looking at the systemlogs I can't help but notice that at the time of forced reboot there were multiple processes killed by a TERM statement for multiple getty processes. Is this a cause for concern? What does getty do?

Edit2: A second check of the logs reveals this for all reboots, but the only thing noticeably different for the unknown process reboot is something to do with the x-session-manager and some CRITICAL messages. (Is it safe to post these kinds of messages? I never know what's safe and what's not from logs.)

---

### Post by cariboo on 2009-08-12
It would help if you post snippets of the log that concern you, just make sure your external ip address doesn't show up in any of the snippets.

---

### Post by risingsun on 2009-08-12
Well, I think the main bits that appear to be relevant are:

x-session-manager[processid]: WARNING: Running '/usr/bin/gconftool-2 --shutdown' at logout returned an exit status of '15'

and after a subsequent restart but right before the second shutdown (when the unknown process popped up) it contains:

x-session-manager[processid2]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed 
x-session-manager[processid2]: WARNING: Client '(null)' failed to reply before timeout 
x-session-manager[processid2]: CRITICAL: gsm_client_peek_app_id: assertion `GSM_IS_CLIENT (client)' failed
x-session-manager[processid2]: CRITICAL: gsm_client_get_app_name: assertion `GSM_IS_CLIENT (client)' failed
x-session-manager[processid2]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed 

(I think those are OK to post, I can't identify anything critical in them. I even took the process number out though that's probably excessive :) )

I'm not sure if these show up anything other than an errant process though, so any clarification would be much appreciated. I was thinking perhaps the error code of 15 might be related, though if it is it would be across a reboot.

---

### Post by unspawn on 2009-08-13
As the syslog "x-session-manager[PID]" identifier shows this is about he Gnome Session Manager (hence GSM_.*). searching the forums will show these types of warnings aren't uncommon and while it's critical in the sense that it should't emit errors (but deal with them instead) these syslog lines unfortunately don't tell you anything about any "unknown processes". Because processes are volatile and don't survive a reboot and because GNU/Linux by default does not log process details *that* extensively, with a default setup it is nigh impossible to find information about something that has died a reboot ago.

---

### Post by risingsun on 2009-08-13
That does appear to be very true, the above was the closest I could find (and it's inclusion here was mainly because of the get_app_name...failed line) to anything unusual. I suppose it's likely it was just an errant process hanging (though I can't really posit why it displayed as "Unknown") since it hasn't occured again.

Out of curiousity, what does exit code 15 for gconftool translate to? I was just wondering if it indicates an error that may have had an impact or was unrelated.

Many thanks again.

---

### Post by unspawn on 2009-08-13
Sorry, I haven't got any clue as it would involve knowing the gconftool-2 source, what it is supposed to do on "--shutdown" and how it handles exceptions.

---

