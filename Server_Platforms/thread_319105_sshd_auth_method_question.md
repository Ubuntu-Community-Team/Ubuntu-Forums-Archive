---
title: "sshd auth method question"
date: 2006-12-15
forum: Server Platforms
---

### Post by hanrai on 2006-12-15
I have searched the internet for a while, but can't find the answer for my question.

I just want to know, is it possible to config sshd in this way:

If an authorized_keys file is available for a user, sshd uses key pair based authentication, password authentication is disabled in this case;
Otherwise sshd uses password authentication method, until this user creates an authorized_keys file.

So users can choose which way they would like to use by themselves.

:rolleyes:

---

### Post by chrisfay on 2006-12-15
If I'm understanding you correctly, you want sshd to accept 'both' keys and passwords. Since passwords is the default, all you need to do is activate the keys option, though I'm unsure of your reasoning behind this.

Usually enabling key based authentication is used in place of passwords to remove the possibility of brute force attacks on the system. It seems counterintuitive to provide both methods.

---

### Post by hanrai on 2006-12-15
Thank you chrisfay.
At present, I have disabled the password authentication in my server. So users can only access it with key based authentication. 

But the problem is I have to help new users to setup their key file. And some users complain that key based authentication is not convenient enough, and want to login with only password.

So I think, if sshd can check if there's an authorized_keys available will be greate. If this file is available password authentication will be disabled automatically. It means if a user have already create a public key in their home directory, they can only login with key authentication method, password authentication will not be possible for him.
And if a user don't like to use key authentication method, they don't need to create the public key file, then the password authentication method will be actived for him.

And another advantage is that I don't need to help them to setup key file. They can do it by themselves. That will be great for me.

---

### Post by chrisfay on 2006-12-15
> And if a user don't like to use key authentication method, they don't need to create the public key file, then the password authentication method will be actived for him.

This sounds great in theory but, it completely underminds the reasoning behind key based authentication.  Why go to the trouble of configuring keys for a few users when others are allowed to authenticate via passwords; and what would be the point of blocking a user who holds a key from password authentication? 

Whether you allow one user or a hundred to authenticate using passwords, you're nullifying any benefit from the added security of key based authentication. You should either force your users to auth via keys, or completely drop the idea and just use passwords. It's like spending a grip on the ultimate padlock for your home but only the people who feel it conveniant enough to use it do. The rest use a tiny little lock. It may be more conveniant, but completely useless regarding the ultimate goal of security.

> So I think, if sshd can check if there's an authorized_keys available will be greate. If this file is available password authentication will be disabled automatically. It means if a user have already create a public key in their home directory, they can only login with key authentication method, password authentication will not be possible for him.

The only difference between enabling both authentication methods and what your proposing is the attempt to block key holders from using passwords and visa versa.  Passwords and keys do virtually the same thing, the defining factor being the level of security provided. Blocking one from the other is absolutely pointless. Your focus should be instead on which method to use, and not on how to integrate them both. IMHO

If you absolutely insist on the setup, the best way to lock users into either method would be to create keys for those who should use keys and accounts for those who should use passwords.  As long as you don't create an account for a key holder, their key will be the only way they can get in. Password users obviously won't have a key so they're automatically locked from the key option. Explicitly blocking either method isn't necessary since one negates the other.

---

### Post by hanrai on 2006-12-18
Thank you Chrisfay. I can understand, but my situation is:
We have about 1000 normal users, and about 20 managers. 
Our normal users don't have so much computer knowledge, so for them, key based authentication is so hard to understand and use. And the security problem for them will not be a big problem, because they have not so much rights, and can do only few things in the server. Their job is to log in server with ssh, and use a special designed program to report their jobs.
But for managers, they know how to use key based authentication, and they know the private key file is so important for them. They have higher privilege, can access crucial data in the server.

I want to leave password authentication method open for normal user, because I don't want to manage so many keys, and they always lost their private key. And every 3 months I have to add hundreds of keys into system.

I want to close password authentication method for managers, after all a key is much longer than a password, and hard to guess.

So I need to setup openssh in this way.

---

