---
title: "UFW rule - did I break something?"
date: 2014-04-28
forum: Security
---

### Post by npinn001 on 2014-04-28
So I found out that UFW was blocking access to the network on my virtual bridge. I disabled UFW and it worked fine, so I did some googling and found that if I put this in the before.rules file I could get it to work.

```
# allow bridge networking
-I FORWARD -m physdev -–physdev-is-bridged -j ACCEPT


```

Except I missed off the first dash on the --physdev line so it only had one -. 

```
# allow bridge networking
-I FORWARD -m physdev –physdev-is-bridged -j ACCEPT


```


When I logged in there was a long delay each time before allowing me in, almost as though somnething was broken. Virt manager remote display wouldnt work either.

Did I break something fundamental or would the firewall have worked other than this?

I have now removed the line and changed /etc/default/ufw to:

```
DEFAULT_FORWARD_POLICY="ACCEPT"
```



Also, I only have localhost access to the server, my router has no open ports forwarded to the server, so presumably even if it was broken there wouldnt be a risk?

Thanks

---

