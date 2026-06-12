---
title: "Automatic updates"
date: 2005-10-19
forum: Server Platforms
---

### Post by billiejoex on 2005-10-19
I would like that my server automatically updates itself via apt every day. 
Are there specific packages that permit me to do this or do I have to manually write a script managed by crond?

Thanks in advance.

---

### Post by majikstreet on 2005-10-19
[QUOTE=billiejoex]I would like that my server automatically updates itself via apt every day. 
Are there specific packages that permit me to do this or do I have to manually write a script managed by crond?

Thanks in advance.[/QUOTE]
I imagine you could create a cron job for that, but I don't think there will be many updates after a while.....

I can't really answer any questions about cron, as I have never used it and have _very_ limited knowledge on it.

-m

---

### Post by UbuWu on 2005-10-20
For now you will have to write a script yourself (wouldn't be hard, just apt-get update && apt-get upgrade). Hopefully the next ubuntu release has an option for automatic upgrades in the update manager.

---

### Post by Ribs on 2005-10-22
Be warned. apt-get will always ask you if it's okay to proceed when you just run apt-get update, as you don't know what will be upgraded until apt tells you. This is of course no good in a script, as there is no interaction.

To get around this, run apt-get with the -y flag;
apt-get upgrade -y

This will force apt-get to assume you answer 'yes' to all questions, and will allow it to work within a script.

From the man page;
> -y, --yes, --assume-yes,
              Automatic  yes to prompts; assume "yes" as answer to all prompts and run non-interactively. If an undesirable situation, such as changing
              a held package, trying to install a unauthenticated package or removing an essential package occurs then apt-get will  abort.  Configura&#8208;
              tion Item: APT::Get::Assume-Yes.

---

