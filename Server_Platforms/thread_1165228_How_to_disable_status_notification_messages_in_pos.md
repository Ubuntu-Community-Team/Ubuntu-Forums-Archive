---
title: "How to disable status notification messages in postfix"
date: 2009-05-20
forum: Server Platforms
---

### Post by adaniels on 2009-05-20
Hi all,

I'm setting up a backup MX server using postfix. The problem is that is generating backscatter when an e-mail address doesn't exist. I simply want to drop undeliverable mail and not send bounce messages. I'm using permit_mx_backup_networks to decide which recipients should be accepted.

The only solution I can find on mailing lists and forums is to not accept the mail in the first place, by checking the recipient address. This is an impossibility, since the addresses should be checked at the exact server that this MX server is backing up. Updating a list on the backup server is also not a feasible solution.

The only settings that comes close is soft_bounce. This turns all 5xx codes into 4xx codes, which is not what I want. Also no mail is dropped.

Does anyone have a solution?

Thanks,
Arnold

---

