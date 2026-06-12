---
title: "reboot command in script"
date: 2011-05-24
forum: Server Platforms
---

### Post by Z.K. on 2011-05-24
I have a script I wrote which checks a cell connection and if it is not there, it will reboot the machine so the cell can come back up in a connected condition.

The problem is I need to be root to run the reboot command from my script.  I have tried running the update-rc.d commands, but when rebooting it just hangs so I was trying to use it as a startup application, but then it needs to be root to run the reboot command.

It is on a remote machine so no I cannot enter the sudo password as I would have no access to the machine in question.  I tried putting it in the rc.local file, but it seems to have the same issue.

Anyone have any ideas?

:confused:

---

### Post by CharlesA on 2011-05-24
You can use sudo reboot in the script.

If you don't want it to prompt for a password, you can edit the /etc/sudoers file.

See [here]("https://help.ubuntu.com/community/RootSudo") for more info.

---

### Post by Lars Noodén on 2011-05-25
> **CharlesA said:**
> You can use sudo reboot in the script.

If you don't want it to prompt for a password, you can edit the /etc/sudoers file.

See [here]("https://help.ubuntu.com/community/RootSudo") for more info.

+1 for sudo

```
%users  ALL=(ALL) NOPASSWD: /sbin/shutdown
```

Of course you'll want to substitute the group "users" with the actual group you are using for your script.

---

### Post by Z.K. on 2011-05-25
> **CharlesA said:**
> You can use sudo reboot in the script.

If you don't want it to prompt for a password, you can edit the /etc/sudoers file.

See [here]("https://help.ubuntu.com/community/RootSudo") for more info.

I was kind of wondering if I needed to do that, but I was concerned about the security aspect of it.  Is there a way to do this for all users, but not give users sudoer rights?  What I am after is a way to run the script, but not give users sudoer in normal users.

I am thinking possibly of creating a hidden user and group and then create a symbolic link to the reboot command with access only for this group or user.  Then I could add this user to the sudoer file.  Do you think this would work?

---

### Post by Lars Noodén on 2011-05-25
> **Z.K. said:**
> I was kind of wondering if I needed to do that, but I was concerned about the security aspect of it.  Is there a way to do this for all users, but not give users sudoer rights?  What I am after is a way to run the script, but not give users sudoer in normal users.

I am thinking possibly creating a hidden user and group and then create a symbolic link to the reboot command with access only for this group or user.  Then I could add this user to the sudoer file.  Do you think this would work?

Sudoers woud be the way to do it.  Make a group for this special activity put the users you want into it and then edit /etc/sudoers:

```

%rebooters  ALL = (ALL) NOPASSWD: /sin/shutdown

```

In that example the group 'rebooters' can use shutdown as root without password, but nothing else and no one else.

---

### Post by Z.K. on 2011-05-25
> **Lars Noodén said:**
> Sudoers woud be the way to do it.  Make a group for this special activity put the users you want into it and then edit /etc/sudoers:

```

%rebooters  ALL = (ALL) NOPASSWD: /sin/shutdown

```

In that example the group 'rebooters' can use shutdown as root without password, but nothing else and no one else.

Thanks, that is what I was looking for.

---

### Post by CharlesA on 2011-05-25
> **Z.K. said:**
> Thanks, that is what I was looking for.
Minor correction: It should be sbin, instead of sin.

---

### Post by Lars Noodén on 2011-05-25
Here is another variation:

```

%rebooters  ALL = (ALL) NOPASSWD: /sin/shutdown, /sbin/reboot

```

---

