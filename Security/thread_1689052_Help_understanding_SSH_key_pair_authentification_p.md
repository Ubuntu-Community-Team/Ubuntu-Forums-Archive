---
title: "Help understanding SSH key pair authentification process"
date: 2011-02-16
forum: Security
---

### Post by Jim_in_Germany on 2011-02-16
Hi,

I'm just trying to understand the process of connecting to a host using my public key via ssh. So far:

I have generated a public / private key pair.
I have stored my public key in the 'authorized_keys' file on the host.
I can successfully connect to the host using this key pair.

However, I am not sure how the key pair authorization / logon process works in detail. What does the host do when it receives my connection? Which side sends what and in which order? Could someone maybe explain this to me or point me in the direction of an article which does so in plain English.

I tried Googling and also Wikipedia, but in the articles I discovered, I found the explanation of this step of the process to be either too complicated or lacking.

Thanks very much in advance.

---

### Post by bodhi.zazen on 2011-02-16
That is a very broad question.

Start with the "basic" articles and then read the more "advanced" ones.

If you have a specific question ask, but how are we to know from your post what you understand and what you do not ?

---

### Post by Jim_in_Germany on 2011-02-17
> That is a very broad question.
It's not really that broad, rather, poorly phrased. Sorry about that!

To be more specific, what I am doing is using PUTTY to access a remote server using a previously generated public private key pair for authentication.

When I click on 'open' (i.e. connect) in PUTTY, I want to know what is taking place between PUTTY and the server.

I spent quite a while Googling yesterday and was able to answer my own question ([http://the.earth.li/~sgtatham/putty/0.55/htmldoc/Chapter8.html]("http://the.earth.li/~sgtatham/putty/0.55/htmldoc/Chapter8.html")): 

So you generate a key pair on your own computer, and you copy the public key to the server. Then, when the server asks you to prove who you are, PuTTY can generate a signature using your private key. The server can verify that signature (since it has your public key) and allow you to log in.

Cheers anyway.

---

### Post by CharlesA on 2011-02-17
Basically it sends your private key to the server and it verifies that it matches the private key that goes with a public key (key-pair) on the server. If it's not the right private key, the server rejects the authentication and disconnects you.

There is no "signature" being generated, it's all based on the private key that is being used.

---

### Post by Hawkoon on 2011-02-17
> **CharlesA said:**
> Basically it sends your private key to the server and it verifies that it matches the private key that goes with a public key (key-pair) on the server. If it's not the right private key, the server rejects the authentication and disconnects you.

There is no "signature" being generated, it's all based on the private key that is being used.


You don't send the private key, it wouldn't be private anymore, right?

Say someone wants to connect to the ssh server as user X. The ssh server will send back a challenge (or signature), the client encrypts it with its private key, it is sent back to the server who then uses public key of user X to decrypt it. If the result matches the originally sent out challenge, than the client claiming to be X is indeed X, and access is granted.

---

### Post by Jim_in_Germany on 2011-02-19
> **Hawkoon said:**
> You don't send the private key, it wouldn't be private anymore, right?

Yeah, that's what I was thinking.
I thought the entire point of a private key is that it never has to be sent over the network.

Thank you for your explanation of the authentication process. I understand it a lot better now.

---

