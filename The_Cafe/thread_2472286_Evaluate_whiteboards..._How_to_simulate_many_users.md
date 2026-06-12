---
title: "Evaluate whiteboards... How to simulate many users?"
date: 2022-02-23
forum: The Cafe
---

### Post by civilpolisen on 2022-02-23
I've set up a server with three different software solutions to evaluate different whiteboards.
Criteria says "At least 150 participants can have the board open simultaneously".

It says... "At least 60 persons can work on the board simultaneously". 

What's the easiest way to simulate this much traffic!? My server is currently in our LAN but I can put it on Internet if there is a service that demands it.

---

### Post by TheFu on 2022-02-23
Do you have 150 friends or employees?  That would be the simplest, for some values of "simple".

Or use an automation tool like **cnee**.  Record a user doing things for 15 minutes, then setup users so that same recording gets started for each user added 20 seconds apart for 60 users.  Enjoy.

If this is a 1-time test for code maintained by other people ... that's all I would do. If this is going to be a service offered to many people outside the company, then I'd use test automation to fully test every possible situation, especially changing screen resolutions timing updates so that all allowed users try to modify the same areas concurrently and that boundaries all work correctly for any sort of allowed input - text, paint, lines, highlighter, whatever.

Some of these tools may not like multiple connections from a single client session, so you may need to simulate different clients sessions using containers or other cname-based kernel constraint systems.  I use firejail.

---

### Post by civilpolisen on 2022-02-24
Thank you for a high quality post! Very much appreciated! I live in Sweden and we need to prepare a suit of tools for public use... Oh, I don't know these words in English! So far, it's an "unnamed project" and name will eventually be assigned later on.

---

