---
title: "&quot;worm&quot; in Thunderbird/Dapper"
date: 2007-05-11
forum: Server Platforms
---

### Post by Barney on 2007-05-11
One of those "You have received a postcard!" messages was opened in Thunderbird (ver 1.5.0.10)/in Dapper; the url was copied from the "click here" and entered into Firefox to go there and take a peek.  What came up was a .bin file to be downloaded - operation was cancelled, bad file was not downloaded.

Now, Thunderbird doesn't receive new messages, as sent, but inserts old messages from ??? into new message body (not the correct message).

Looks like a worm, acts like a worm, in Thunderbird; how can I get rid of it?

Yes, I know -very dumb- to not have deleted the suspect message in the first place!

Barney

---

### Post by mvaniersel on 2007-05-11
Well, unless you were running thunderbird as superuser, it's unlikely your system got messed up. All that could have happened is that your profile got messed up.

Your profile is in /home/yourname/.mozilla-thunderbird. It's in a directory that's named with a lot of random characters plus .default (.e.g aus9123213.default). Back it up (to save your email) and then delete it, then you'll get a fresh profile. You can copy the mailbox files over from your backed up profile to the new one. The mailbox files are just text, so they can't contain the worm.

You do keep your system up-to-date don't you?

---

### Post by Barney on 2007-05-11
System has regularly been updated with Synaptic.  ...running since last September.

I backed up my T-Bird profile; tried to start Thunderbird again, and got the message: "Mozilla-Thunderbird is already running, but it is not responding.  To open a new window, you must first close the existing Mozilla-Thunderbird process, or restart your system."

"System Monitor" did not show T-Bird running, however, I restarted the system, and same thing again, "...Thunderbird is already running...." but it wasn't.

Using Synaptic, I completely removed Thunderbird and reinstalled it - same thing: "...Thunderbird is already running...."

Suggestions?

---

### Post by konungursvia on 2007-05-11
Look for a taskbar of TB and xkill it, or kill the process with your sys monitor, to make sure.

---

### Post by Barney on 2007-05-11
Nothing related to TB in Sys Monitor to kill.

---

### Post by Barney on 2007-05-11
I deleted default profile and created new default; and TB has started - working on it now.

---

### Post by Barney on 2007-05-11
However many hours later..................

I finally found that my Inbox was corrupted: as found at-> Account Settings/Server Settings/Local Directory, where I had created my own storage directory in Documents (so that when I 'backup' I backup everything by backing up Documents.

Fortunately, I had backed things up on 4/30/07, so only lost 11 days of Inbox stuff.

Since my Inbox corruption occured at nearly, or exactly, the same time as I was playing around with that damn "You have received a post card !" incoming message, I must confess that this was probably another damn fool oerator error, doing what I have advised all not to do.

Thunderbird is good, but obviously not "fool" proof.

---

### Post by slimdog360 on 2007-05-12
thats pretty cool, so do you really think it really was a worm or something else? Install calmav or something, run a virus scan and see what you get. Im really interested.

---

### Post by Barney on 2007-05-12
I feel very nearly certain that it was the email message, almost 100% known to carry a worm (from searching the Inet), that I was messing around with, trying to find from whence it came, that caused the problem with my inbox, corrupting it.

Thunderbird may be good, but it's not invulnerable to such malicious invasions.

I did install ClamAV, and scanned everything, everhwhere - nothing was detected.  This is not surprising, as worms are not technically viruses, and in many cases are harder to eradicate - or so my internet searches have explained.

In searching the "Inbox" that was corrupted, I found several files as "program" types - not to be found in another machine side by side with the affected machine, running the same version of Thunderbird.

---

### Post by slimdog360 on 2007-05-13
Was the url that you clicked on something like this? wwwfriendgreetings.com (note to people: dont put that into your browser cause it could be virusfied)

I was reading about something similar you described here from the trendmirco site. I was saying that the email didn't contain anything bad, but the url that you clicked on was the bad thing. Hence Thunderbird would not to blame. Perhaps you should look into activating spam assassin to go with thunderbird.
 
[http://www.trendmicro.com/vinfo/virusencyclo/default5.asp?VName=WORM_FRIENDGRT.B]("http://www.trendmicro.com/vinfo/virusencyclo/default5.asp?VName=WORM_FRIENDGRT.B")

I did find something else which sounds more like the one you got from here [http://www.spywarehunter.org/entry/sophos-warns-of-hackers-spreading-trojan-horse-via-mix-of-email-and-web/]("http://www.spywarehunter.org/entry/sophos-warns-of-hackers-spreading-trojan-horse-via-mix-of-email-and-web/")
but it says that this one is a trojan which downloads as a .exe file, so its unlikely that it is it. However it does say this one comes from an email with the subject: You have received a postcard!  
so maybe it was a coincidence or a variant?

---

### Post by Barney on 2007-05-25
The "worm" has returned today.  I can't find anything wrong in the Thunderbird file structure, or anything that looks awry in where I've stored messages.

Anyone have any ideas on how to rid Thunderbird of this worm?

Barney

---

### Post by Barney on 2007-05-25
I should have added that the worm replaces any incoming message with a message that can't be found, that I sent on 01/14/2006!

---

### Post by Barney on 2007-05-26
The "worm" has returned after 2 1/2 weeks, and replaces all my incoming mail with an old mail message sent to my nephew on 1/14/2006 or an old valid card notification from jacquielawson.com (cards).  ClamAV doesn't find anything; and I can't find any mysterious "program" files in my mail storage this time.

Any help on "worm" eradicationf from T-Bird?

---

