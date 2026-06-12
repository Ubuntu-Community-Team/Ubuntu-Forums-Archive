---
title: "help with apache2 and ssl?"
date: 2009-08-13
forum: Server Platforms
---

### Post by rhcm123 on 2009-08-13
I am at a complete loss. I've been trying to get apache2 and ssl working for over 2 days now, with no luck. i had it working perfectly as I wanted before, but an electrical storm knocked out my main disk, and i hadn't backed up my apache configs (despite having them working for over 8 months).

I want the following to happen:
1. All traffic coming in on port 80 gets redirected to 443.
2. Squirrelmail is enabled and only accepts connections over 443. (I can't get that working at all)

I've included the following config files that i think i've setup properly, but i don't know how to setup a virtual server, or how to make a site, and i need help with that.

I've also included /var/www/index.php, the main page, if it helps.
EDIT: I had to rename the files to upload them to ubuntuforums, they aren't called that on the server.

---

### Post by Bachstelze on 2009-08-13
Instead of posting your config files as attachments, paste them in your message with CODE tags around them. That will make them easier to read.

---

### Post by rhcm123 on 2009-08-13
> **HymnToLife said:**
> Instead of posting your config files as attachments, paste them in your message with CODE tags around them. That will make them easier to read.

I just posted them all as .txt files because i didn't want to open them all, copy the text, etc. instead just right click the file then hit "open in new tab". that should work fine.

---

### Post by Bachstelze on 2009-08-13
> **rhcm123 said:**
> I just posted them all as .txt files because i didn't want to open them all, copy the text, etc. instead just right click the file then hit "open in new tab". that should work fine.

Good luck getting help. If you don't want to bother copying the contents of a bunch of text files, people won't be inclined to help you.

Oh and by the way, no, it doesn't work.

---

