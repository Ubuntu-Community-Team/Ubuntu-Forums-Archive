---
title: "Possible Spyware installed in Ubuntu 8.04"
date: 2009-02-09
forum: Security
---

### Post by sirhalos on 2009-02-09
My father originally used to use Windows XP until he out of no where got spyware on his computer. I ran a few different spyware programs to get as much out as I could but some odd things kept happening so I gave up and forced Ubuntu down his throat.

He’s been running Ubuntu 8.04 LTS for months now and loves it and he has been doing all the updates (as far as I know).

This weekend I received a call from him claiming he some how got spyware again. He *cough* ‘claims’ he went to the Sun Times website and was reading a news story when all of a sudden a porn site came up. He ‘claims’ anytime he clicked on anything the site would come back up. He ‘claims’ he forced shutdown his laptop then turned his laptop back on and opened up Firefox again. He ‘claims’ that he received the standard Ubuntu Firefox homepage and whenever he clicked on anything or went anywhere the porn site would come back up again. Then he claimed that if he clicked anything on the porn site it would bring up a new Firefox window with the standard Ubuntu Firefox homepage.

As anyone heard of this at all?

I had him just bring up a Terminal window and do rf –rf .mozilla which did fix the problem but can anyone think of what may have happened?

The only thing I could think of is he had a Firefox window open but he was minimized through javascript or very small which was opening the windows and it was not him clicking at all. Then when he forced the laptop to shutdown and he reopened Firefox it just brought up his last websites visited. That sound possible? Anyone know of any spyware on Firefox in Ubuntu at all? Maybe he thought he was shutting down Firefox but he was just closing the open windows and one was still opening but minimized. 

My father works as a Senior Mainframe Engineer so he is not a complete idiot with computers but he is not the best in desktop environments. Anyone heard anything like this at all?

---

### Post by cdenley on 2009-02-09
I think most browser exploits that exist in firefox in windows also exist in firefox for linux. Regardless of what OS you're using, I would suggest using noscript, which almost certainly would have prevented your issue, if a website he visited did in fact manage to alter his firefox profile.
```

sudo apt-get install mozilla-noscript

```

---

### Post by tubbygweilo on 2009-02-09
sirhalos,
If NoScript is taken in conjunction with Adblock Plus and FlashBlock (I know it takes a bit of time to construct the associated white lists) then I feel that your father is heading towards a safer surfing experience and that is good for the both of you.

---

### Post by sirhalos on 2009-02-09
Yea I could possibly put Adblock Plus on for him but I think he wouldn't understand NoScript since it can disable a lot of things. He already complains about that one site out of a million that his video doesn't work on. All these things I have thought about just thought it was amazing that something like this happened and looking for possibilties to how it could have happened. If he wasn't so freaked out and wanting it fixed right then that second I would have told him to not do anything until I looked at it so I could try to figure out what could have happened. I still feel the some how Firefox was still running when he thought he closed it since he said when he opened it back up his Ubuntu Homepage was still there instead of a website changing his default page to a porn site. My guess is always that when he turned his laptop back on since he forced it to turn off Firefox said would you like to start up Firefox with the last page viewed since the force shutdown? And he clicked yes bringing the site back up. Just seeing if anyone has heard anything else that could have done this as a security concern.

---

### Post by bodhi.zazen on 2009-02-09
This kind of thing is not uncommon and the solution is to either create a new profile in Firefox or learn to use NoScript + Adblock ;)

---

