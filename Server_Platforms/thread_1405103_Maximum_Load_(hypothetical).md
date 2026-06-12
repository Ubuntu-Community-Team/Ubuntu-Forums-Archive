---
title: "Maximum Load (hypothetical)"
date: 2010-02-12
forum: Server Platforms
---

### Post by Porter200el on 2010-02-12
So I have a question about running LAMP on ubuntu server, I have ran 9.10 and LAMP for awhile, but I was wondering hypothetically what the maximum load for the server would be with the following specs:

ubuntu server 9.10
PIII 500 Mhz
512 MB of RAM
Running a broadband connection 1 Mbps upload

Just looking for ballpark numbers

---

### Post by Kiwi76 on 2010-02-12
It almost solely depends on what you'll be running and doing. Any server will be able to handle more users with static web pages than with multiple sites, applications, scripts, etc. What will you be using it for?

---

### Post by Porter200el on 2010-02-12
> **Kiwi76 said:**
> It almost solely depends on what you'll be running and doing. Any server will be able to handle more users with static web pages than with multiple sites, applications, scripts, etc. What will you be using it for?

I am running a cms (drupal) and serving up some small classified ads, to get relatively minimal traffic.  I have run this setup before for  a personal site, but I am going to eastimate 100 hits per day max, which I feel like this setup could easily handle.  I figured I would ask the community because it is such a good resource.

---

### Post by Kiwi76 on 2010-02-12
It should be fine, although I do admit I don't know all too much about Drupal and it's demands. Regardless, it should handle it if it won't get too many hits. I have a site with comparable or maybe fewer hits (a few static HTML pages and a MyBB PHP/MySQL powered community), and it fares well in the server in the signature (I realize it's more powerful, but RAM usage and such indicates it's easily work within something like what you're going to be using).

Edit: Seems I've underestimated my site's hits lately. It was in the sixties the other day after averaging around the forties, but it's at 121 unique (not repeat) for the last twenty-four hours, and that includes the community forums only, not the website itself. Still, it goes to show how little you'll be able to get away with. You should be more than fine.

---

### Post by Porter200el on 2010-02-12
> **Kiwi76 said:**
> It should be fine, although I do admit I don't know all too much about Drupal and it's demands. Regardless, it should handle it if it won't get too many hits. I have a site with comparable or maybe fewer hits (a few static HTML pages and a MyBB PHP/MySQL powered community), and it fares well in the server in the signature (I realize it's more powerful, but RAM usage and such indicates it's easily work within something like what you're going to be using).

Edit: Seems I've underestimated my site's hits lately. It was in the sixties the other day after averaging around the forties, but it's at 121 unique (not repeat) for the last twenty-four hours, and that includes the community forums only, not the website itself. Still, it goes to show how little you'll be able to get away with. You should be more than fine.

Excellent, Thank you for sharing that, I thought it would be the case, but that is the beauty of the Ubuntu community, you ask a question and you get an answer.  I appreciate your time and help, Thanks!

---

