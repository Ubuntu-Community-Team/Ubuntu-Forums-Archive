---
title: "Once again I have to rip and replace"
date: 2018-06-29
forum: Ubuntu Cloud and Juju
---

### Post by quartzeye on 2018-06-29
For some unknown reason, I can no longer update the metadata in Horizon.  I can use the CLI and do all that I want but not in the dashboard.

[ATTACH=CONFIG]280246[/ATTACH]

When I look at the logs in the Horizon container I don't see any relevant error other than

[Fri Jun 29 15:58:33.720613 2018] [wsgi:error] [pid 1765:tid 140200077539072] [remote 10.89.13.111:54968] UserWarning: Using keystoneclient sessions has been deprecated. Please update your software to use keystoneauth1.


When I look at Keystone logs I see this:

(keystoneclient.common.cms): 2018-06-29 16:05:59,281 ERROR Signing error: Unable to load certificate - ensure you have configured PKI with "keystone-manage pki_setup"
(keystone.common.wsgi): 2018-06-29 16:05:59,283 ERROR Command 'openssl' returned non-zero exit status 3
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/keystone/common/wsgi.py", line 226, in __call__
    result = method(req, **params)
  File "/usr/lib/python2.7/dist-packages/keystone/common/controller.py", line 82, in inner
    return f(self, request, *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/keystone/auth/controllers.py", line 361, in revocation_list
    CONF.signing.keyfile)
  File "/usr/lib/python2.7/dist-packages/keystoneclient/common/cms.py", line 336, in cms_sign_text
    signing_key_file_name, message_digest=message_digest)
  File "/usr/lib/python2.7/dist-packages/keystoneclient/common/cms.py", line 384, in cms_sign_data
    raise subprocess.CalledProcessError(retcode, 'openssl')
CalledProcessError: Command 'openssl' returned non-zero exit status 3


I have yet to find anything helpful to fix this.  So now my only option seems to be to complete trash the entire environment and rebuild it from scratch as this did work when I initially installed the stack

Also, there doesn't seem to be an active monitoring of issues for these things as it takes days to get a response from anyone, if at all.

---

