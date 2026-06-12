---
title: "Ubuntu pcs cluster authentication and its not generating any token"
date: 2018-03-01
forum: Server Platforms
---

### Post by bibhutitosh on 2018-03-01
I am facing issues with pcs cluster authentication and its not generating any token for it in /var/lib/pcsd/token. any solution? I am using pcs-0.9.149 

```
root@vubuntu-s:~/scripts# pcs cluster auth vubuntu-s -u hacluster -p passwd --force --debug
Running: /usr/bin/ruby -I/usr/share/pcsd/ /usr/share/pcsd/pcsd-cli.rb auth
--Debug Input Start--
{"username": "hacluster", "local": false, "nodes": ["vubuntu-s"], "password": "passwd", "force": true}
--Debug Input End--
Return Value: 0
--Debug Output Start--
{
  "status": "ok",
  "data": {
    "auth_responses": {
      "vubuntu-s": {
        "status": "bad_password"
      }
    },
    "sync_successful": true,
    "sync_nodes_err": [

    ],
    "sync_responses": {
    }
  },
  "log": [
    "I, [2018-03-01T14:58:22.718695 #20059]  INFO -- : PCSD Debugging enabled\n",
    "D, [2018-03-01T14:58:22.718754 #20059] DEBUG -- : Did not detect RHEL 6\n",
    "I, [2018-03-01T14:58:22.718795 #20059]  INFO -- : Running: /usr/sbin/corosync-cmapctl totem.cluster_name\n",
    "I, [2018-03-01T14:58:22.718822 #20059]  INFO -- : CIB USER: hacluster, groups: \n",
    "D, [2018-03-01T14:58:22.728536 #20059] DEBUG -- : [\"totem.cluster_name (str) = debian\\n\"]\n",
    "D, [2018-03-01T14:58:22.728628 #20059] DEBUG -- : []\n",
    "D, [2018-03-01T14:58:22.728667 #20059] DEBUG -- : Duration: 0.009699932s\n",
    "I, [2018-03-01T14:58:22.728761 #20059]  INFO -- : Return Value: 0\n"
  ]
}
--Debug Output End--

Error: vubuntu-s: Username and/or password is incorrect
root@vubuntu-s:~/scripts#
```

---

