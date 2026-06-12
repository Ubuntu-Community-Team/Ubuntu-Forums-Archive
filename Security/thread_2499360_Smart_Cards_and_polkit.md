---
title: "Smart Cards and polkit"
date: 2024-07-24
forum: Security
---

### Post by originaltrini0 on 2024-07-24
Hello all:

I am setting up an Ubuntu 24.04 server with [step-ca]("https://smallstep.com/docs/step-ca/") and a Nitrokey [HSM2]("https://shop.nitrokey.com/shop/nkhs2-nitrokey-hsm-2-7#attr=").
I created a system account to run the CA and discovered that the system user could not access the HSM2, but the root user could.

After digging around, I came across polkit. I configured a drop-in file, and now my system user can access the HSM2.

My question:
Is polkit the correct mechanism to authorize a local system account to the smart card framework?
I am just looking for validation or to know if there is a better way of accomplishing the goal.
The server is managed over an SSH session.

More information can be found at Nitrokey's [forum]("https://support.nitrokey.com/t/unpriviledged-service-account/6369/4").

Thanks

---

### Post by currentshaft on 2024-07-24
What is a "drop-in file" that you configured?

What do you mean by authorization? You can use udev rules to grant non-root users access to /dev devices.

I typically use scdaemon/pcscd to manage my smart cards.

---

### Post by originaltrini0 on 2024-07-24
Hey, @currentshaft.  Thanks for responding.

Here is more context:
I had an issue running a CA (step-ca) as a system account where the private keys are on an HSM (Nitrokey HSM 2).
Everything worked as it should have if I had run the CA as root.

After some help from the folks at Nitrokey with debugging, it was found that the system account was being denied access to the smart card:
```

47974690 winscard_msg_srv.c:256:ProcessEventsServer() Common channel packet arrival
00000079 winscard_msg_srv.c:267:ProcessEventsServer() ProcessCommonChannelRequest detects: 13
00000016 pcscdaemon.c:132:SVCServiceRunLoop() A new context thread creation is requested: 13
00014180 auth.c:143:IsClientAuthorized() Process 18482 (user: 999) is NOT authorized for action: access_pcsc
00000380 winscard_svc.c:355:ContextThread() Rejected unauthorized PC/SC client
00000111 winscard_svc.c:1096:MSGCleanupClient() Thread is stopping: dwClientID=13, threadContext @0xaaab02363e70
00000018 winscard_svc.c:1104:MSGCleanupClient() Freeing SCONTEXT @0xaaab02363e70

```

```

# sudo -H -u step bash -c 'step-ca /etc/step-ca/config/ca.json'
badger 2024/07/23 12:57:44 INFO: All 1 tables opened in 3ms
badger 2024/07/23 12:57:44 INFO: Replaying file id: 0 at offset: 9973
badger 2024/07/23 12:57:44 INFO: Replay took: 474.441µs
error initializing PKCS#11: could not find PKCS#11 token
#
#
# step-ca /etc/step-ca/config/ca.json
badger 2024/07/23 12:58:09 INFO: All 1 tables opened in 2ms
badger 2024/07/23 12:58:09 INFO: Replaying file id: 0 at offset: 9973
badger 2024/07/23 12:58:09 INFO: Replay took: 547.347µs
2024/07/23 12:58:19 Building new tls configuration using step-ca x509 Signer Interface
2024/07/23 12:58:19 Starting Smallstep CA/ (linux/arm64)
2024/07/23 12:58:19 Documentation: https://u.step.sm/docs/ca
2024/07/23 12:58:19 Community Discord: https://u.step.sm/discord
2024/07/23 12:58:19 Config file: /etc/step-ca/config/ca.json
2024/07/23 12:58:19 The primary server URL is https://example.com:443
2024/07/23 12:58:19 Root certificates are available at https://example.com:443/roots.pem
2024/07/23 12:58:19 X.509 Root Fingerprint: d<REDACTED>a
2024/07/23 12:58:19 Serving HTTPS on :443 ...

```

I found [this]("https://www.redhat.com/en/blog/controlling-access-smart-cards"), which led me down the polkit idea. I was also referred to read [this]("https://blog.apdu.fr/posts/2023/11/pcsc-lite-and-polkit/"), as it seems as if polkit may have been gating access to smart cards via pcsc since late last year.
I added this file to /etc/polkit-1/rules.d/step.rules and I was successful with the system account using the HSM:
```

polkit.addRule(function(action, subject) {
    if (action.id == "org.debian.pcsc-lite.access_pcsc" &&
        subject.user == "step") {
            return polkit.Result.YES;
    }
});

polkit.addRule(function(action, subject) {
    if (action.id == "org.debian.pcsc-lite.access_card" &&
        action.lookup("reader") == 'Nitrokey Nitrokey HSM (DENK03018290000         ) 00 00' &&
        subject.user == "step") {
            return polkit.Result.YES;    }
});

```

So while things are working, I want to validate if "this is the way".

Thanks

---

### Post by currentshaft on 2024-07-24
I'm not very familiar with Nitrokeys, but in general, if you're using this system as a single user dedicated for a single purpose (manage an HSM), and the system is otherwise protected (full volume encryption, network policy, OS hardening, etc.) then there's really no issue with running your (known and presumed trusted) software as root.

---

