---
title: "pycryptopp  /var/mail/optparse Crypto.Cipher Crypto.Hash"
date: 2011-07-03
forum: Security
---

### Post by iiiears on 2011-07-03
pycryptopp asks for path /var/mail/ Why is this? :-?

Removed Postfix some time ago.
installed telnetable.py
installed python-pycryptopp_0.5.17-1+b1_amd64.deb

Ran telnetable.py w/o rebooting. -- Oops, errors!
pycryptopp asks for path /var/mail/

/home/GPL-3.0/telnetenable.py: line 21: import: command not found
/home/GPL-3.0/telnetenable.py: line 22: import: command not found
/home/GPL-3.0/telnetenable.py: line 23: import: command not found
from: can't read /var/mail/optparse
from: can't read /var/mail/Crypto.Cipher
from: can't read /var/mail/Crypto.Hash
/home/GPL-3.0/telnetenable.py: line 28: TELNET_PORT: command not found
/home/GPL-3.0/telnetenable.py: line 38: syntax error near unexpected token `('
/home/GPL-3.0/telnetenable.py: line 38: `def ByteSwap(data):'
root@GPL-3.0:~# '/home/GPL-3.0/telnetenable.py' "192.168.1.1 00062513C918"/home/GPL-3.0/telnetenable.py: line 21: import: command not found
/home/GPL-3.0/telnetenable.py: line 22: import: command not found
/home/GPL-3.0/telnetenable.py: line 23: import: command not found
from: can't read /var/mail/optparse
from: can't read /var/mail/Crypto.Cipher
from: can't read /var/mail/Crypto.Hash
/home/GPL-3.0/telnetenable.py: line 28: TELNET_PORT: command not found
/home/GPL-3.0/telnetenable.py: line 38: syntax error near unexpected token `('
/home/GPL-3.0/telnetenable.py: line 38: `def ByteSwap(data):'

---

