---
title: "Resetting Password created new account?"
date: 2013-11-09
forum: Resolution Centre
---

### Post by gimfred2 on 2013-11-09
[COLOR=#232323][FONT=Verdana]On attempting to access the Ubuntu Forums for the first time in a long time my password/account combination didn't work despite using a password manager for several years, probably due to the security incident. It is believed that it was reset soon after, but whatever. Last access was in April.[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]Upon using and responding to the "Forgotton Password" once the password reset form was completed I got given a new login account? gimfred2? It appears to be using the same email address as the original account which I thought would cause a conflict. As I can't access the original account to check the preferred email account I'm at a loss how to correct this.[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]

[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]The account I would like to access is: 
[http://ubuntuforums.org/member.php?u=260994](http://ubuntuforums.org/member.php?u=260994) gimfred joined 2007

I can't find the original email account for setup but I do have a email address change from 2009 (x 2) complete with Activation IDs. Not that they are likely to be useful.[/FONT][/COLOR]

---

### Post by coffeecat on 2013-11-10
I'm not sure how you tried to use your old username/password combination because the old vbulletin login method has been removed and replaced with SSO login. Forum passwords are irrelevant now, and were randomised after the security breach. The only password that matters now for forum login is the password you use to log into your Ubuntu One account. 

> **gimfred2 said:**
> Upon using and responding to the "Forgotton Password" once the password reset form was completed I got given a new login account? gimfred2? It appears to be using the same email address as the original account which I thought would cause a conflict. As I can't access the original account to check the preferred email account I'm at a loss how to correct this.

You need to understand something: Ubuntu One accounts and forum accounts are entirely separate entities, hosted on different servers. The only connection is the link that is created between a single Ubuntu One account and a single forum account to enable login to the forum from Ubuntu One SSO. The forgotten password link must have been the Ubuntu One link - there is no forum forgotten password link. Resetting your Ubuntu One password was not the reason the system created a new forum account. It was because the emails in the old forum account and the Ubuntu One account did not match. Your preferred email is the Ubuntu One email and you can change this in your Ubuntu One account.

> **gimfred2 said:**
> I can't find the original email account for setup but I do have a email address change from 2009 (x 2) complete with Activation IDs. Not that they are likely to be useful.

They would indeed be useful, but let me help you with this. The email you used in Ubuntu One to login is of the form [email]string@domain.com[/email]. The latest email in the gimfred account is of the form [email]string+ubuntu@domain.com[/email]. Same "string" and same domain, the only difference is the "+ubuntu". Change your preferred email in Ubuntu One to the +ubuntu form and then post back. Simply changing it won't enable you to log into the old account just yet - I will have to disassociate this forum account from Ubuntu One first. But I won't disassociate it until you post back to confirm that you have successfully changed the Ubuntu one email because if you log in before you have read this post and changed your email, you will simply re-associate your Ubuntu One account with this account.

---

### Post by gimfred2 on 2014-01-19
Thanks for that info. I now have the +ubuntu inserted between string and domain in the preferred email.

Are the emails required? What is the preferred process of sharing them? (Not keen on sharing as an attachment.)

I just have to access that account from home. (I have a particular problem at work that keeps bringing me back to the ubuntu forums. But my email provider for that account is blocked at work.)

---

### Post by Iowan on 2014-01-19
I disassociated this account from SSO. Hopefully, your next login will connect you with your old account. When (if?) that happens, you are free to change either/both email accounts and the link should remain intact. Good luck!

---

### Post by Iowan on 2014-01-19
I notice **gimfred** has logged back in, so I'll disable the **gimfred2** account.

---

