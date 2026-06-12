---
title: "landscape-api sync-mirror-pocket release jammy ubuntu failed"
date: 2023-05-17
forum: Ubuntu Cloud and Juju
---

### Post by lacid2 on 2023-05-17
I created series for jammy on my Landscape server with the following command:
```

landscape-api create-series \
  --pockets release,updates,security \
  --components main,restricted,universe,multiverse \
  --architectures amd64,i386 \
  --gpg-key mirror-key \
  --mirror-uri http://archive.ubuntu.com/ubuntu/ \
  --mirror-series jammy jammy ubuntu --json | jq

```

When I run **landscape-api sync-mirror-pocket release jammy ubuntu** I get the following error:
```

ERROR: Condition '40976EAF437D05B5|3B4FE6ACC0B21F32' not fulfilled for './lists/update-jammy_jammy_InRelease'.

Signatures in './lists/update-jammy_jammy_InRelease':

'871920D1991BC93C' (signed 2022-04-21): missing pubkey

Error: Not enough signatures found for remote repository update-jammy (http://archive.ubuntu.com/ubuntu jammy)!

There have been errors!

```
I did not have this issue when I synced the pockets on the same server for "focal", any ideas?

---

### Post by lacid2 on 2023-05-17
Importing the key from [https://keyserver.ubuntu.com/pks/lookup?search=871920D1991BC93C&fingerprint=on&op=index](https://keyserver.ubuntu.com/pks/lookup?search=871920D1991BC93C&fingerprint=on&op=index) solved this issue
- created Release.gpg with the content of [this file]("https://keyserver.ubuntu.com/pks/lookup?op=get&search=0xf6ecb3762474eda9d21b7022871920d1991bc93c"), downloaded from the page above
- landscape-api import-gpg-key ubuntu-archive-signing-key Release.gpg
- run
```

landscape-api create-series \
  --pockets release,updates,security \
  --components main,restricted,universe,multiverse \
  --architectures amd64,i386 \
  --gpg-key mirror-key \
  --mirror-uri http://archive.ubuntu.com/ubuntu/ \
  --mirror-gpg-key ubuntu-archive-signing-key \
  --mirror-series jammy jammy ubuntu --json | jq
```

---

