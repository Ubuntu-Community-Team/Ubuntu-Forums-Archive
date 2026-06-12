---
title: "fetchmail and aliases"
date: 2007-02-25
forum: Server Platforms
---

### Post by Koybe on 2007-02-25
Hello,

Here is a strange question :

Someone as an external pop mailbox with some aliases on it. I would like to fetch it but rearrange mails localy regarding to these aliases as if it was dirrefrent mailboxes. Is it possible?

Thank you.

---

### Post by jtc on 2007-02-25
Yeah, it should be. Take a look at procmail.

---

### Post by Koybe on 2007-02-25
Thank you. It's a little short but I've done some searching. Procmail looks a bit difficult to me and I don't understand what's intersting for me to use it as I already got postfix/courier/fetchmail.

I foudn this in the fetchmail documentation :
> 
 Here&#8217;s what a simple retrieval configuration for a multidrop mailbox looks like: 
  
  poll pop.provider.net:
        user maildrop with pass secret1 to golux &#8217;hurkle&#8217;=&#8217;happy&#8217; snark here

 This says that the mailbox of account &#8217;maildrop&#8217; on the server is a multidrop box, and that messages in it should be parsed for the server user names &#8217;golux&#8217;, &#8217;hurkle&#8217;, and &#8217;snark&#8217;.  It further specifies that &#8217;golux&#8217; and &#8217;snark&#8217; have the same name on the client as on the server, but mail for server user &#8217;hurkle&#8217; should be delivered to client user &#8217;happy&#8217;.

It looks like what i want to do but I'm not sure the users they're talking about on the distance mailbox are ok. Because they aren't really users but basicly only aliases.

I think i need to try this with some testing mailbox if I can get one becasue otherwise it can be a mess in the mails :)

---

