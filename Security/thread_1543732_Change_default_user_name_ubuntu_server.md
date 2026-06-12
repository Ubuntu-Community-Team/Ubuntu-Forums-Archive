---
title: "Change default user name ubuntu server"
date: 2010-08-01
forum: Security
---

### Post by raashell on 2010-08-01
I installed Ubuntu Server and want to change the default user name to increase the difficulty of accessing the server.  Is it possible to do this?  If not, can I effect the same change by creating a new user and transferring over permissions, files, and etc.?

---

### Post by FuturePilot on 2010-08-01
There is no default username.

---

### Post by raashell on 2010-08-01
Sorry, I'm referring to the initial user I set up.  I want to change the username from someting like, "sam" to something resembling a password.

---

### Post by Bachstelze on 2010-08-01
> **raashell said:**
> I want to change the username from someting like, "sam" to something resembling a password.

No, you don't.  There is absolutely no point in doing that, and it might break a lot of things.

---

### Post by raashell on 2010-08-01
Bachstelze,

Thanks for the advice.  My rationale is that the bots probing my server are using common names to attempt to guess a user / password combination.  I'm thinking that changing the user name to something far outside of this scope would make the guessing game much tougher.  I assume that you know considerably more about this than me though, would you mind briefly telling me what's wrong with this approach?

J

---

### Post by Ryan Dwyer on 2010-08-01
Chances are any bots that try to brute force a server login will only try root. Any other accounts would take far longer to brute force and might not even be an admin.

I wouldn't worry about it. But if you're paranoid you can monitor your auth log to see if anyone's trying to log in with the correct username.

---

### Post by FuturePilot on 2010-08-01
Instead of changing your username to avoid bots, you should use something like fail2ban or denyhosts. They are much more effective than changing a username.

---

### Post by raashell on 2010-08-01
If most attacks are coming at root, then I can see how changing the user might be too much effort/problems for too little gain.  I do have denyhosts running so it's good to hear that it is a recommended approach.  Thanks again for sharing your knowledge and expertise.  -J

---

