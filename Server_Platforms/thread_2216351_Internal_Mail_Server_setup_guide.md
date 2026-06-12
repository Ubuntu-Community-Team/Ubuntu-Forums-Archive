---
title: "Internal Mail Server setup guide"
date: 2014-04-11
forum: Server Platforms
---

### Post by rizsilverthorn2 on 2014-04-11
Hi there,

Trying to figure out the correct search term to find guidance on the following situation, potentially with a setup guide. Finding lots of external email server guides, internal only email server guides, but nothing matching what I'm looking for.

Scenario:
We have several email addresses (sales@domain.com, [EMAIL="ebay@domain.com"]ebay@domain.com[/EMAIL], [EMAIL="other@domain.com"]other@domain.com[/EMAIL], [EMAIL="another@gmail.com"]another@gmail.com[/EMAIL]), each which are accessed by several people in the company using POP3 in Outlook. Due to restrictions on the external server, we often get locked out because of too many simultaneous connections. What I was thinking of was having a single server on the local network grabbing all of the emails from the external servers (our own hosted email server and gmail). Each internal client would then connect to the local server and fetch mails from there. Each external mail account must be kept separate. Our internet connection is also barely faster than dialup, so having multiple (10+) clients downloading the same, sometimes 4MB+ emails makes for a slow experience.

We then need to be able to send messages from [EMAIL="sales@domain.com"]sales@domain.com[/EMAIL], [EMAIL="ebay@domain.com"]ebay@domain.com[/EMAIL], [EMAIL="other@domain.com"]other@domain.com[/EMAIL], [EMAIL="another@gmail.com"]another@gmail.com[/EMAIL] from each internal client. Does anyone have a link to a guide for this type of scenario? I have set up postfix, dovecote as an external mailserver before, but that was 10+ years ago, and a different situation.

Does anyone have a link to a solution? Looking at setting up an Ubuntu 12.04 LTS server if that helps.

Thanks in advance,
Fred

---

### Post by SeijiSensei on 2014-04-11
> **rizsilverthorn2 said:**
> What I was thinking of was having a single server on the local network grabbing all of the emails from the external servers (our own hosted email server and gmail). Each internal client would then connect to the local server and fetch mails from there.

Ironically the solution is to run "[fetchmail]("https://library.linode.com/email/fetchmail")" on your server.

> We then need to be able to send messages from [EMAIL="sales@domain.com"]sales@domain.com[/EMAIL], [EMAIL="ebay@domain.com"]ebay@domain.com[/EMAIL], [EMAIL="other@domain.com"]other@domain.com[/EMAIL], [EMAIL="another@gmail.com"]another@gmail.com[/EMAIL] from each internal client.

Thunderbird lets you to define multiple "identities" to use as your From address (Edit > Account Settings > Manage Identities).  You select the appropriate sender address from a drop-down box at the top of the composition window.  I know the ancient Eudora had this ability as well, so I wouldn't be surprised to see other mail clients like Evolution support identities.

---

### Post by rizsilverthorn2 on 2014-04-14
Hi [COLOR=#000000]SeijiSensei,

Thanks for the answer - will be trying to figure that out this week. Now I know *what* I'm looking for, makes it a lot easier! I figured the sending would not be an issue, just the receiving.

Regards,
Fred[/COLOR]

---

