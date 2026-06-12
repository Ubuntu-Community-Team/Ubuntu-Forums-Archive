---
title: "Configuring ircd-irc2 server?"
date: 2005-04-28
forum: Server Platforms
---

### Post by martijntje on 2005-04-28
I have set up ircd-irc2 on my server, however i am having some trouble configuring it to give me operator privileges.

I have looked through the manpages and the example configuration file and have come up with the following O:line (password hash removed of course)

```
O:127.0.0.1/32:passhash:martijn::2:A
```

When i use the /oper command, it asks for my password, which is accepted, so there everything goes well, however, if i try to use my almighty mod powers, it tells me that i do not have operator privileges in the given channel.

According to the example config file, the A flag should give me 'all possible permissions'.

Can anyone help me out on this?

---

