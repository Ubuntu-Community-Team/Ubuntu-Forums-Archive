---
title: "Ruby and crontab"
date: 2006-06-06
forum: Server Platforms
---

### Post by sig_UVa on 2006-06-06
So I have a ruby script that works when I run **ruby auto_sync.rb** from the /var/www/quickbase/sae_sync/ directory


I want to run this as a cron so I use crontab -e and add the text below:

*/5 * * * * /var/www/quickbase/sae_sync/ruby auto_sync.rb

I get 

/bin/sh: /var/www/quickbase/sae_sync/ruby: No Such File or Directory

If I remove the ruby command and do:

*/5 * * * * /var/www/quickbase/sae_sync/auto_sync.rb

I get 

/bin/sh: /var/www/quickbase/sae_sync/auto_sync.rb: Permission Denied 

in my log.

Any ideas?  I appreciate the help!

---

### Post by alaithea on 2006-06-06
I had a similar problem recently. I was trying to run a ruby script at system start with a shebang line of ```
#!/usr/bin/env ruby
```. It would work when I called it at the command line, but it was saying it couldn't find ruby when it rebooted. Solution: I symlinked my actual ruby binary, which was at /usr/bin/ruby1.8, to /usr/bin/ruby. Moral of the story: take a look at your shebang line.

---

### Post by sig_UVa on 2006-06-06
Hi alaithea,

Thank you for the response.  I changed the shebang line to #!/usr/bin/env ruby1.8

Do I have to do the symlink also?


Thanks!

---

### Post by alaithea on 2006-06-07
That will work, but for portability and future upgradability issues, I'd recommend the symlink instead of changing the shebang line. If, for some reason, ruby is no longer called ruby1.8 on your system and your script breaks, it's better to only need to change one symlink than the shebang line in one or many files.

---

### Post by sig_UVa on 2006-06-07
Ahh, I see.  Thank you for your help!

---

### Post by Skeletor on 2008-04-05
There is a symlink for me from ruby to ruby1.8 in my own login.  What context is cron calling ruby in though?  If I put a "which ruby >> /home/username/cron.log 2>&1" in crontab, I see that it gives an error for finding ruby (it does find ruby1.8).  So what kind of symlink did you add to fix this?  Please be exact.

---

### Post by Skeletor on 2008-04-05
So I see now the link should be: "sudo ln /usr/bin/ruby1.8 /usr/bin/ruby".
My question should have been:
My login by default finds ruby in /usr/local/bin/ruby, why doesn't the context that cron is run in find things in /usr/local/bin/?  What configuration is there for the "cron user"?  (The user that cron runs as.)

---

