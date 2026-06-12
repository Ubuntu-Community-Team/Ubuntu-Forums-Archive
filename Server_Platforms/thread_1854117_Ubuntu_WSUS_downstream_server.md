---
title: "Ubuntu WSUS downstream server"
date: 2011-10-03
forum: Server Platforms
---

### Post by Chrus on 2011-10-03
This is probably going to seem like an odd request, but I thought I'd throw it out there anyway and see what I get back.

We've got a couple of small business clients who run Windows SBS 08/11 in their main office. Their branches have no servers, so we've set them up with a couple of ubuntu boxes that do routing and VPN's and a few other fancy things.

So the problem I'm seeing is that whenever I release windows updates, each user at the branches is pulling them over the WAN from the SBS server. Now if there were a windows server in the branches I could set them up as downstream servers and clients would pull updates from the local server.

Is it at all possible to set up an ubuntu server to act as a WSUS downstream server? Would be good if i could push the updates to the branches once rather than having each client machine pull the updates seperatly over the WAN.

---

### Post by kleverbear on 2011-10-03
Not to knock on ubuntu but for Win domains try [calculate-linux.org]("http://www.calculate-linux.org/")

Oh and you will need to make lots of registry edits and entry's to get this going. I'm not sure of what will be needed for win7 but there are some templates for XP to make the correct hacks in the registry. If you feel advatures make sure u back up the reg in win. 

Or you can virtulize a 2003 wsus in Ubuntu... just food for thought

---

### Post by Chrus on 2011-10-04
Thanks Kleverbear, but changing distros now isnt really an option. Already have a few of these ubuntu boxes out there. Im really after a solution to run on Ubuntu.

What do you mean by virtulize WSUS? Do you mean run virtualbox with a win server VM and have WSUS on that? Or is there a way to just virtulize the WSUS components?

---

