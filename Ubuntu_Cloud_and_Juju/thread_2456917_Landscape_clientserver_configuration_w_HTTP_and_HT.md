---
title: "Landscape client/server configuration w/ HTTP and HTTPS proxy..."
date: 2021-01-21
forum: Ubuntu Cloud and Juju
---

### Post by jamesmartens on 2021-01-21
Doing a proof of concept configuration of Landscape (on prem), and having several issues, mostly around the http/https proxy configuration for the server and clients.

I have the Landscape server (name: landscape) configured under Settings, "Proxy for HTTP and HTTPS traffic" as (not the real IP here, of course) as [http://w.x.y.z:8181](http://w.x.y.z:8181), and "No proxy for" 127.0.0.1, localhost.

The landscape clients, of course, are registered and can see the landscape server, and have the ssl_public_key set in /etc/landscape/server.pem.

I can see process information in the 'computers' section of Landscape, however, when I go to check 'packages' on any of the registered systems, I get the following error: OOPS ID: OOPS-63da1937e3bab2aa829cf4d936618f88

As we don't have this under support (as of yet, as it's a POC, and we're evaluating it to see if it does what we want before we pay for it), Ubuntu support won't assist. Urk. The engineers passed a message along through the sales rep saying that it didn't appear the proxy was set correctly, but with no other information.

We have the http_proxy/https_proxy env variable set on the clients so HTTP requests normally will go through the proxy (for everything not Landscape) but we don't want requests for the Landscape server to go through the proxy as it's (obviously) internal. In apt.conf on the clients we've set the following so that works, but it appears the clients are having issues sending information through to the landscape server.

Acquire::http::Proxy {
landscape DIRECT:
};

The error in the appserver.log is listed below (off the Landscape server /var/log/landscape-server/appserver.log file)

Jan 21 20:39:15 appserver-1 ERR  Dumping OOPS-63da1937e3bab2aa829cf4d936618f88.
Jan 21 20:39:15 appserver-1 ERR  [https://landscape/account/standalone/computer/9/packages/index.html](https://landscape/account/standalone/computer/9/packages/index.html) request_id=1c8f74e5-8707-4675-84c5-357ad1d84aab#012Traceback (most recent call last):#012  File "/usr/lib/python2.7/dist-packages/zope/publisher/publish.py", line 129, in publish#012    obj = request.traverse(obj)#012  File "/usr/lib/python2.7/dist-packages/zope/publisher/browser.py", line 560, in traverse#012    ob = super(BrowserRequest, self).traverse(ob)#012  File "/usr/lib/python2.7/dist-packages/zope/publisher/http.py", line 457, in traverse#012    ob = super(HTTPRequest, self).traverse(obj)#012  File "/usr/lib/python2.7/dist-packages/zope/publisher/base.py", line 260, in traverse#012    obj = publication.traverseName(self, obj, entry_name)#012  File "/usr/lib/python2.7/dist-packages/zope/app/publication/zopepublication.py", line 198, in traverseName#012    ob2 = adapter.publishTraverse(request, nm)#012  File "/opt/canonical/landscape/canonical/routes/publisher.py", line 137, in publishTraverse#012    view = queryMultiAdapter((self.context, request), name=name)#012  File "/usr/lib/python2.7/dist-packages/zope/component/_api.py", line 123, in queryMultiAdapter#012    return sitemanager.queryMultiAdapter(objects, interface, name, default)#012  File "/usr/lib/python2.7/dist-packages/zope/interface/registry.py", line 359, in queryMultiAdapter#012    objects, interface, name, default)#012  File "/usr/lib/python2.7/dist-packages/zope/interface/adapter.py", line 541, in queryMultiAdapter#012    result = factory(*objects)#012  File "/opt/canonical/landscape/canonical/landscape/ui/package/dashboard.py", line 70, in __init__#012    if self._has_no_packages:#012  File "/usr/lib/python2.7/dist-packages/zope/cachedescriptors/property.py", line 71, in __get__#012    value = func(inst)#012  File "/opt/canonical/landscape/canonical/landscape/ui/package/dashboard.py", line 118, in _has_no_packages#012    no_packages_count = self._computer_counts["no-packages"]#012  File "/usr/lib/python2.7/dist-packages/zope/cachedescriptors/property.py", line 71, in __get__#012    value = func(inst)#012  File "/opt/canonical/landscape/canonical/landscape/ui/package/dashboard.py", line 109, in _computer_counts#012    return self._counts[0]#012  File "/usr/lib/python2.7/dist-packages/zope/cachedescriptors/property.py", line 71, in __get__#012    value = func(inst)#012  File "/opt/canonical/landscape/canonical/landscape/ui/package/dashboard.py", line 105, in _counts#012    return self._search.get_computer_counts()#012  File "/opt/canonical/landscape/canonical/landscape/model/package/search.py", line 221, in get_computer_counts#012    counts = self._get_computer_counts_external()#012  File "/opt/canonical/landscape/canonical/landscape/model/package/search.py", line 301, in _get_computer_counts_external#012    account_id=account_id, computer_ids=computer_ids)#012  File "/opt/canonical/landscape/canonical/landscape/model/package/client.py", line 38, in query#012    return self._query(method, params)#012  File "/opt/canonical/landscape/canonical/landscape/model/package/client.py", line 60, in _query#012    raise PackageSearchRequestError(loads(error.body)["Error"])#012  File "/usr/lib/python2.7/json/__init__.py", line 339, in loads#012    return _default_decoder.decode(s)#012  File "/usr/lib/python2.7/json/decoder.py", line 364, in decode#012    obj, end = self.raw_decode(s, idx=_w(s, 0).end())#012  File "/usr/lib/python2.7/json/decoder.py", line 382, in raw_decode#012    raise ValueError("No JSON object could be decoded")#012ValueError: No JSON object could be decoded


Anyone have any suggestions?

---

