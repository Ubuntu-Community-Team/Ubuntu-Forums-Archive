---
title: "Service and firestarter"
date: 2005-03-23
forum: Server Platforms
---

### Post by mirtux on 2005-03-23
Hi,
  i'm on a net in which the server is running with a M$ (*sic*) os. I'm using firestarter as a firewall in my Debian laptop. I've seen in the "events" tab that the service *microsoft-ds* tried to access my system from port 445. Does anybody of you knows about this? What kind of service is this?

Thanks,
MC

---

### Post by az on 2005-03-23
445 SMB (NetBIOS over TCP)

---

### Post by mirtux on 2005-03-23
Hi,
  so it is normal that i'm seeing it?

Thanks,
MC

---

### Post by jdong on 2005-03-23
Yes -- It's caused when that Microsoft system tries to talk to your system via SMB. It could happen because:

1. Periodical NetBIOS name updates
2. User error (typed in wrong IP into Windows Explorer)
3. Moon phases -- full moons may cause more probes on port 445

It's normal and harmless.

---

### Post by mirtux on 2005-03-24
Thanks for you help jdong!
I think that my point is connected to 1) (or more probably to 3)....8-))


Regards,
MC

---

