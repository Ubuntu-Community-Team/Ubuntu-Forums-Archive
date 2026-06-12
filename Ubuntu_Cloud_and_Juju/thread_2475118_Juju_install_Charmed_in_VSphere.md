---
title: "Juju install Charmed in VSphere"
date: 2022-05-17
forum: Ubuntu Cloud and Juju
---

### Post by pherbst01 on 2022-05-17
Hi all

Trying to install charmed in vsphere. Have set up a dedicated datacenter, according to [https://juju.is/docs/olm/vmware-vsphere](https://juju.is/docs/olm/vmware-vsphere)

Add cloud and credential works perfect, but accessing the specified folder in add credential does not seem to work - tried several combinations, all with no success.
the error i get is

 [COLOR=#242424][FONT=-apple-system]14:22:06 ERROR juju.cmd.juju.commands bootstrap.go:884 failed to bootstrap model: folder path "/Datacenter/vm/kubetest" not found

the folderstructure in vsphere is /Datacenter/vm/[/FONT][/COLOR][COLOR=#242424][FONT=-apple-system]kubetest, in add-credential i've added with [/FONT][/COLOR][COLOR=inherit][FONT=&quot]Enter vmfolder [/FONT][/COLOR][COLOR=inherit][FONT=&quot]([/FONT][/COLOR][COLOR=inherit][FONT=&quot]optional[/FONT][/COLOR][COLOR=inherit][FONT=&quot])[/FONT][/COLOR][COLOR=inherit][FONT=&quot]: [/FONT][/COLOR][COLOR=#242424][FONT=-apple-system]kubetest/

any help would be appreciated!

Best
Peter

[/FONT][/COLOR]

---

