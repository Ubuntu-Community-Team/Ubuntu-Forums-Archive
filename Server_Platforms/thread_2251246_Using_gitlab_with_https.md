---
title: "Using gitlab with https"
date: 2014-11-02
forum: Server Platforms
---

### Post by Raner on 2014-11-02
I didn't know where to quite put this post because it is about a server, but not on ubuntu server, but just ubuntu 14.04 LTS (desktop).

I have followed the instructions to install gitlab from: [https://about.gitlab.com/downloads/](https://about.gitlab.com/downloads/). Git lab works, and I can access it from [http://gitlab-myvm](http://gitlab-myvm) (which strangly redirects me to just gitlab-myvm in the browser).

I then followed every command here to try to generate a server.key and a server.crt file: [https://help.ubuntu.com/10.04/serverguide/certificates-and-security.html](https://help.ubuntu.com/10.04/serverguide/certificates-and-security.html). (from the "[SIZE=2][FONT=arial]Generating a Certificate Signing Request (CSR)" section to the "[/FONT][/SIZE][SIZE=2][FONT=arial]Installing the Certificate" section (inclusive)[/FONT][/SIZE])

I ran the following commands in order:
```
openssl genrsa -des3 -out server.key 1024
openssl rsa -in server.key -out server.key.insecure
mv server.key server.key.secure
mv server.key.insecure server.key
openssl req -new -key server.key -out server.csr
openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt
sudo cp server.crt /etc/ssl/certs
sudo cp server.key /etc/ssl/private
```

So far so good, no errors.I then followed the gitlab guide to getting https working:[https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/README.md#enable-https](https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/README.md#enable-https)

I set my external url to the following in my gitlab.rb file:
```
external_url "https://gitlab-myvm"
```

And use the following commands:
```
sudo mkdir -p /etc/gitlab/ssl
sudo chmod 700 /etc/gitlab/ssl
sudo cp gitlab-myvm.key gitlab-myvm.crt /etc/gitlab/ssl/

sudo gitlab-ctl reconfigure

sudo ufw allow https
```

I add the following line to my gitlab.rb file:
```
nginx['redirect_http_to_https'] = true
```

Then finally did:
```
sudo gitlab-ctl reconfigure
```

So I thought I would be done here and I could go to [https://gitlab-myvm](https://gitlab-myvm), but I get an "Unable to connect" error. Surprisingly, [http://gitlab-myvm](http://gitlab-myvm) still works.

I have never setup an https server before and am fairly unfamiliar with linux (windows background), but need to setup gitlab for development purposes. Any help would be greatly appreciated.

---

