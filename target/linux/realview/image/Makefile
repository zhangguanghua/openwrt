#
# Copyright (C) 2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/image.mk

define Image/BuildKernel
	cp $(KDIR)/$(subst ",,$(KERNELNAME)) $(BIN_DIR)/openwrt-$(BOARD)-vmlinux.elf
endef

define Image/BuildKernel/Initramfs
	cp $(KDIR)/$(subst ",,$(KERNELNAME))-initramfs $(BIN_DIR)/openwrt-$(BOARD)-vmlinux-initramfs.elf
endef

define Image/Build/squashfs
    $(call prepare_generic_squashfs,$(KDIR)/root.squashfs)
endef

define Image/Build
	$(call Image/Build/$(1))
	dd if=$(KDIR)/root.$(1) of=$(BIN_DIR)/openwrt-$(BOARD)-root.$(1) bs=128k conv=sync
endef

$(eval $(call BuildImage))
