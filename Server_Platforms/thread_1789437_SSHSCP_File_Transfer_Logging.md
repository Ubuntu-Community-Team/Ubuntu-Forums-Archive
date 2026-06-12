---
title: "SSH/SCP File Transfer Logging"
date: 2011-06-23
forum: Server Platforms
---

### Post by sauce345 on 2011-06-23
I have searched these forums and others for this ability.  They are some references from a few years ago but nothing solid that I can make out of them.  I still cannot figure out how to see what files are transferred by my users over scp.  There was a patch that I saw you could apply and it would enable logging but its rather outdated.  Its got to be something simple that I can turn on.  For instance turning up the log levels or something...  

And for you quick haters, I know simply adding scp logging wouldn't suffice to capture all events if someone new what they were doing. Example: Cat a file and pipe its output over SSH.  But my users are not advanced and this is of no concern to me.

So I call out to your SSH/SCP gurus..give me the solution that I know is right in front of my face!!

---

### Post by Dangertux on 2011-06-23
I think you answered your own question already. 

OpenSSH 5.3 (the version in the repos) supports logging of scp/sftp. So yes turning up your logging would work fine for what you seem to want to do. 

Also I believe that the patch you are referring to only disables them from using a terminal , if you mean the scponly shell. 
Am I missing something here? Are you wanting to see more then just the files being transferred?

---

### Post by sauce345 on 2011-06-23
Ya I was grepping my /var/log/auth.log for the wrong thing and I finally just went through it by hand and their it was.  I think also didn't think it would be in the auth.log because other distros talked about it going into /var/log/messages.  Thanks for the reality check!

Also it was kind of fun turning the log level to VERBOSE and watch what directories they traverse through. :)

---

### Post by Dangertux on 2011-06-24
Yeah, no problem glad it worked out for you.

---

