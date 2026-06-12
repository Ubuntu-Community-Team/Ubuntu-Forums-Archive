---
title: "Two-factor authentication doesn't work correctly"
date: 2015-05-28
forum: Security
---

### Post by click66 on 2015-05-28
I'm trying to install google-authenticator on my Ubuntu server. I installed the lib via:

    ```
sudo apt-get install libpam-google-authenticator
```

then In my /etc/pam.d/sshd I've added: 

    ```
auth required pam_google_authenticator.so
```

and in my /etc/ssh/sshd_config

    ```
ChallengeResponseAuthentication yes
```

Now when I have public key ssh then it just ask for nothing and it logs in: fine. When I don't have ssh keys on a other computer for example then it must ask me for a verification code and my password so I added this line in my sshd_config:

    ```
AuthenticationMethods publickey keyboard-interactie:pam,password
```

The first problem was with all of this I can't login anymore in my server. The server asks me for a verification code and then my password. When I enter my password I always get Permission denied. So I thought maybe I need to add my user to my sshd_config file so I did like this:

    ```
AllowUsers dirk
```

Still the same problem. When I change this:

    ```
auth required pam_google_authenticator.so 
```
to this:

    ```
auth suffucient pam_google_authenticator.so
```


Then I can login again. But when testing everything I noticed that whatever verification code I enter when I enter my password correct I can still login. 


So anyone who could help me so that my password AND verification code must be correct?

---

