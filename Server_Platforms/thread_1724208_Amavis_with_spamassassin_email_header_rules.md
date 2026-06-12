---
title: "Amavis with spamassassin email header rules"
date: 2011-04-08
forum: Server Platforms
---

### Post by kohdesmond on 2011-04-08
Hi guys,

i need some help here, i tried to create a custom rules in /etc/mail/spamassassin/local.cf

#spam header check
header check_SPAM       SUBJECT =~ /\THIS IS SPAM\b/i
score SPAM_Score 60.0

but amavis does not pick it up and still let the email pass through.

What shall i do, in order to pick up the email as spam ?

Regards

Desmond

---

### Post by venol on 2011-04-24
maybe someone can help us?

---

### Post by SeijiSensei on 2011-04-24
> #spam header check
header check_SPAM SUBJECT =~ /\THIS IS SPAM\b/i
score SPAM_Score 60.0


The score entry must match the header entry like this:

```

header check_SPAM Subject =~ /THIS IS SPAM/
score  check_SPAM 60.0

```

Notice I removed the escape, the blank space, and the "i" modifier to the regex.  The "i" modifier makes the test case-insensitive, but you specified an all-caps string.  Removing the \b ensures that this will match even if there is no trailing space.  Finally I made the score line refer to the check_SPAM rule.

Run "spamassassin -D --lint" after adding or changing rules to see if there are any errors.  "-D" will give you a lot of debugging info.  If that's too overwhelming, just use "--lint" alone.

---

### Post by venol on 2011-04-24
thanks for the reply SeijiSensei. That's solve my problem about spamassassin.

---

### Post by SeijiSensei on 2011-04-25
> **venol said:**
> thanks for the reply SeijiSensei. That's solve my problem about spamassassin.

You're welcome.  You might want to edit your original post and choose "Solved" from the drop-down box.

---

