---
title: "Landscape server - updates via proxy server"
date: 2016-02-24
forum: Ubuntu Cloud and Juju
---

### Post by Eric_Mueller on 2016-02-24
Hello,

I have installed the landscape server using the quickstart package. The server requires a proxy to reach the internet for updates however i am unable to find where i can specify a proxy so that the landscape services can use the proxy for updates.

I have a proxy set in my environment variables and also have a proxy set for the apt-get client, but neither of these seem to support the landscape server services.

declare -x http_proxy="http://proxy-server:8888/"
declare -x https_proxy="http://proxy-server:8888/"

# cat /etc/apt/apt.conf.d/80proxy
Acquire::http::Proxy "http://proxy-server:8888/";

Here are the failures i receive in the landscape-server logs.....

For instance here are some snippets from the landscape-server service logs under /var/log/landscape-server/

Feb 24 22:35:54 usn-script INFO  Connection to AMQP broker failed: localhost: [Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ConnectionRefusedError'>: Connection was refused by other side: 111: Connection refused.#012]

Feb 24 22:33:48 juju-sync-1 ERR  Connection failed#012Traceback (most recent call last):#012Failure: twisted.internet.error.ConnectionRefusedError: Connection was refused by other side: 111: Connection refused.

Feb 24 23:00:16 update-alerts ERR  twisted.internet.error.ConnectionRefusedError: Connection was refused by other side: 111: Connection refused.

I would assume i would need to specify a proxy configuration in the /etc/landscape/service.conf however i cannot find anything supporting this. i would appreciate any help.

Thanks,
Eric

---

