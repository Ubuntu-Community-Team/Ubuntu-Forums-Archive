---
title: "After image delete in openstack dashboard"
date: 2015-06-21
forum: Ubuntu Cloud and Juju
---

### Post by sebastien6 on 2015-06-21
Hi i m bootstraped with openstack, i deleted an image in openstack dashboard and now when i want to deploy a precise charm i have this error :

machine-0: caused by: request ([http://10.1.1.129:8774/v2/65102b378a7d45fb9be1e553c5f78575/servers](http://10.1.1.129:8774/v2/65102b378a7d45fb9be1e553c5f78575/servers)) returned unexpected status: 400; error info: {"badRequest": {"message": "Image 529146c7-4e56-4fb8-9f5d-767b0ed40cf4 is not active.", "code": 400}}

I understand, that is normal because no precise image is available, then i added a new precise image from the openstack dashboard. The upload work, and the image is ready and active.

I think than i need to update the juju config with the new changes do in openstack dashboard, perhaps through the Glance API ?
Thank you for your help.

---

