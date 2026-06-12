---
title: "How do I pitch this?"
date: 2009-04-14
forum: The Cafe
---

### Post by ZarathustraDK on 2009-04-14
Thinking about suggesting some "optimizations" at work, but I'm not really sure how feasable the scenario is. If I'm right, then it could save a bundle, and perhaps pave the way for further switches in order to reduce expenses in other areas as well.

The scenario : about 700 machines currently running WinXP as OS, with a citrix-client (the users only use their remote citrix-desktop, nothing local), and an altiris-agent running, all set up in an Active Directory framework.

What I want to suggest : Use linux instead. Currently they pay the XP-license twice (OEM-price for newly arrived computers, and then bulk-licensing price for every computer configured). Those license-costs could be cut by 1. ordering computers without an OEM-install and 2. using linux instead with a citrix-client installed.

I am not sure about the altiris-agent though. I do believe I saw a linux-version somewhere, but I'm not a 100% sure. Can anyone confirm it exists? (their site is not exactly intuitive)

How about AD? Does/can linux-clients play nice when managed in Active Directory? Or does it take some doing? Impossible?

How much would you gauge the potential savings to be, considering it's OEM and bulk-licenses of WinXP Professional.

---

### Post by bashveank on 2009-04-14
I wouldn't be so sure that buying OS-less computers would be a major savings. Make sure you verify that before pitching anything...

---

### Post by Eisenwinter on 2009-04-14
What is your position at work?

If you have nothing to do with any management, do not suggest anything at all, as they won't listen to you anyway.

You know how many times I've suggested things at work, to improve efficiency, and make the work loads and expenses cheaper and easier?

They haven't listened to me ONCE. They only listen when I say "X is broken, needs a replacement part" or something, and they check it out and buy a new one, or something.

---

### Post by ilrudie on 2009-04-14
Citrix licensing is tricky.  You need Citrix User Licenses and MS CALs (Client Access Licenses).  CALs can be bundled with the OS License and your company may save money using these Licesnes (per seat) rather than buying the server licenses (per server).  Keep licensing in mind when trying to figure this out.

---

### Post by PilotJLR on 2009-04-14
Why rich clients at all?? Why not thin clients? Cost savings comes from reduction in facilities costs (power and cooling) and hardware replacement cycles.

Using a Citrix backend, the logical next step is to move to thin clients.

Nevertheless, a proof of concept is necessary. Even though it works just fine, some users have something like a mental block against using anything non-Windows, even if it's just a launchpad for a remote session. You don't want to be the person that alienates 700 users.

---

### Post by ZarathustraDK on 2009-04-14
> **bashveank said:**
> I wouldn't be so sure that buying OS-less computers would be a major savings. Make sure you verify that before pitching anything...

I know, the savings there are probably minor, but it all adds up. I guess the trick is not to say "then you can save 5$ per computer by doing this" rather "then you can get this (better) hardware instead if you do it this way".

> What is your position at work?

If you have nothing to do with any management, do not suggest anything at all, as they won't listen to you anyway.

You know how many times I've suggested things at work, to improve efficiency, and make the work loads and expenses cheaper and easier?

They haven't listened to me ONCE. They only listen when I say "X is broken, needs a replacement part" or something, and they check it out and buy a new one, or something.

I'm just a regular IT-support grunt, but the place I work at is generally susceptible to logical arguments (though the cogs move slowly sometimes, they do move) ;) . I think, generally speaking, your description applies to private companies, which is not the sector I'm working in (can't say no more :) ).

> Citrix licensing is tricky. You need Citrix User Licenses and MS CALs (Client Access Licenses). CALs can be bundled with the OS License and your company may save money using these Licesnes (per seat) rather than buying the server licenses (per server). Keep licensing in mind when trying to figure this out.

Yeah that stuff is a science in its own right. I'll have to figure that one out. In any case I can say with a straight face that money will be saved as server-CAL's would (in a logical world, of course) cost less than OS-bundled CAL's. It does warrant some investigation though...

> Why rich clients at all?? Why not thin clients? Cost savings comes from reduction in facilities costs (power and cooling) and hardware replacement cycles.

Using a Citrix backend, the logical next step is to move to thin clients.

Nevertheless, a proof of concept is necessary. Even though it works just fine, some users have something like a mental block against using anything non-Windows, even if it's just a launchpad for a remote session. You don't want to be the person that alienates 700 users.

Funny story. We actually did that, but the thin clients we had only had 2 gig of diskspace which got eaten up by winXP (they had to run Altiris you see (yeah, major facepalm, I know, somebody's ears somewhere are very red methinks)).

I am very aware of the mental block :) (oh the stories I could tell...). I figured one could just install some linux and do a citrix passthrough setup with an altiris-agent in the background. It's that altiris-agent which is causing all the headaches it seems, but it HAS to be running.

Any takers on the Altiris/Active Directory side of things?

---

### Post by PilotJLR on 2009-04-14
> **ilrudie said:**
> Citrix licensing is tricky.  You need Citrix User Licenses and MS CALs (Client Access Licenses).  CALs can be bundled with the OS License and your company may save money using these Licesnes (per seat) rather than buying the server licenses (per server).  Keep licensing in mind when trying to figure this out.

TS CAL's are needed regardless of the endpoint, provided we're talking Presentation Server / XenApp hosted apps.

Which is another tangent... they are doing 700 desktops on Presentation Server? Or XenDesktop?

If they are using XD, then moving to a thin client could be disruptive to their VECD licensing, as they would need to move from Software Assurance to Thin Client VECD.

---

