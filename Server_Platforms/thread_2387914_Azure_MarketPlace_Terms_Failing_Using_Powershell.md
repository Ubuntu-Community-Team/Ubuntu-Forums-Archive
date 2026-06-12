---
title: "Azure MarketPlace Terms Failing Using Powershell"
date: 2018-03-25
forum: Server Platforms
---

### Post by amcclimont on 2018-03-25
Hello,

  I am attempting to get the Azure marketplace terms for UbuntuServer using PowerShell, however the command is failing:

```
PS D:\> Get-AzureRmMarketplaceTerms -Publisher Canonical -Product UbuntuServer -Name 16.04-LTS
Get-AzureRmMarketplaceTerms : Offer with PublisherId: {0} and OfferId: {1} not found. If this offer has been created recently, please allow upto 30 minutes for this offer to be available for Purchase. If error persists, 
contact support.
At line:1 char:1
+ Get-AzureRmMarketplaceTerms -Publisher Canonical -Product UbuntuServe ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : CloseError: (:) [Get-AzureRmMarketplaceTerms], CloudException
    + FullyQualifiedErrorId : Microsoft.Azure.Commands.MarketplaceOrdering.Cmdlets.Agreements.GetAzureRmMarketplaceTerms
```

  Is anyone else experiencing this issue, or found a solution to this issue?

Thanks.

---

### Post by wildmanne39 on 2018-03-25
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

