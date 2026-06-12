---
title: "Captive Logins with ssh"
date: 2007-03-15
forum: Server Platforms
---

### Post by TyphoonJoe on 2007-03-15
This is for a text user only server, forget all gui stuff :)

I want to set up captive logins using ssh.  By "captive login" I mean I want text users to be placed into a menu on login, and when the exit the menu they exit Linux.  The solution for now is adding the menu script to $HOME/.profile (this is for ksh, same as bash_profile for bash), followed by an exit.  This works perfectly for text users connecting with telnet.  

With ssh it works, but not fully because the user can always connect from their ssh client using "ssh -t <servername> <command>"  And if they use a remote command of ksh, bash, or some other shell, the user has full Linux command line access.  They simply do not hit the defalt shell at all.  Even if you change /etc/passwd so the default shell is actually a command to the menu script, the user can specify a ssh remote command to gain Linux command line access.  

Though telnet works, it is not at all secure and not a good alternative.  It also seems I could use ssh keys, but I cannot require a key for every user, there are too many and they change too often.  I basically want to have ssh allow shell access but NOT allow remote commands to be run.  Anyone know how to do this????  

Thanks for any ideas!

TyphoonJoe

---

### Post by Frosty Cold Drink on 2007-03-15
What you will want to do is
1. Change the user's shell in /etc/passwd
2. Remove as many shells as possible from /etc/shells
3. Change the ownership and permissions of remaining shells so that these captive users cannot execute any other shells.

---

### Post by TyphoonJoe on 2007-03-15
Frosty,

Thanks for the reply- good points.

1)
The issue is that the shell in /etc/passwd **does not matter**.  The ssh command just executes the Icommand/shell without caring what is defined for your user record.  

2) 
No matter what I need at least one shell for admin users, and even one shell would still be a problem.  And the user needs a shell to execute the captive menu script for the application.

3)  
Again the captive user needs to run something out a shell, so they need some shell access (you can't run a perl script without a shell, as far as I know).

Also- I should mention that even if they don't have access shell they can execute remote commands which can be strung together, essentially giving access.


I looked for ~3 hours before positing, and of course soon after I post I found  a possible solution in OpenSSH 4.4 and higher.  Edgy only lets me go to 4.3, so I may need to go to Feisty (if it has it) or just compile OpenSSH 4.4 or higher myself.

FYI OpenSSH 4.4 introduces "The ForceCommand Directive:"

> The ForceCommand directive forces the execution of the command specified by ForceCommand, ignoring any other command supplied by the client. Previous releases of OpenSSH specified this option in the authorised_keys file. Following is an example of the ForceCommand functionality:
xample 1-2 Example of the ForceCommand Directive

The following line is included in the sshd_config file:
ForceCommand pwd
A user on the client system enters the following command:
# ssh remotehost ls /
In such a scenario, pwd is executed regardless of the ls command executed by the user.


Along with that, they now let you use "Match" syntax to make options apply only to users or groups, so my backup scripts etc. can use remote commands but normal users cannot.   

Thanks agin,
TyphoonJoe

---

