---
title: "journald remote upload issues with TLS"
date: 2022-02-28
forum: Server Platforms
---

### Post by Gibbs on 2022-02-28
Does anyone use TLS with systemd-journal-remote and systemd-journal-upload? On Ubuntu 20.04 (both servers) I keep getting this obscure error reported on the receiver:

```

Stream declares field with size 3512818432485632960 > DATA_SIZE_MAX = 805306368

```

The client/uploader reports the following, which I assume is because of the above:

```

gnutls_handshake() failed: The TLS connection was non-properly terminated

```

Generating the certificates using the example in man systemd-journal-upload results in the same.

---

### Post by kevdog on 2022-03-02
Hmm didn't even know there was such a feature available.  Where are you uploading to?  Are you using self-signed certs?

---

