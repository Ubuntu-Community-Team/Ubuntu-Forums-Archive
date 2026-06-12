---
title: "clamscan error on 17.10"
date: 2017-09-19
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2017-09-19
clamscan -r /
clamscan: /build/llvm-toolchain-3.9-hPFDdS/llvm-toolchain-3.9-3.9.1/lib/IR/Constants.cpp:1902: static llvm::Constant* llvm::ConstantExpr::getGetElementPtr(llvm::Type*, llvm::Constant*, llvm::ArrayRef<llvm::Value*>, bool, llvm::Type*): Assertion `Ty == cast<PointerType>(C->getType()->getScalarType())->getContainedType(0u)' failed.
Aborted
 

any ideas/tks

---

### Post by rburkartjo on 2017-09-23
updates corrected.

---

