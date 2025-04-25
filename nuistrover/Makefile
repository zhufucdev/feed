include $(TOPDIR)/rules.mk
 
# Name, version and release number
# The name and version of your package are used to define the variable to point to the build directory of your package: $(PKG_BUILD_DIR)
PKG_NAME:=nuistrover
PKG_VERSION:=1.0
PKG_RELEASE:=1
HOST_BUILD_DEPENDS:=golang/host
 
# Source settings (i.e. where to find the source codes)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/zhufucdev/nuist_rover.git
PKG_SOURCE_VERSION:=8e400382391e54ce1bf2448a26bc29fe8d1e9406
 
include $(INCLUDE_DIR)/package.mk
 
# Package definition; instructs on how and where our package will appear in the overall configuration menu ('make menuconfig')
define Package/nuistrover
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Rover for NUIST network
endef
 
# Package description; a more verbose description on what our package does
define Package/nuistrover/description
  Rover for NUIST network
endef
 
# Package preparation instructions; create the build directory and copy the source code. 
# The last command is necessary to ensure our preparation instructions remain compatible with the patching system.
define Build/Prepare
		$(Build/Prepare/Default)
endef
 
# Package build instructions; invoke the Go compiler to first compile the source file, and then to link the file into the final executable
define Build/Compile
		GOOS=linux GOARCH=mipsle GOMIPS=softfloat go build -C $(PKG_BUILD_DIR) -ldflags "-w -s" -o $(PKG_BUILD_DIR)/$1
endef
 
# Package install instructions; create a directory inside the package to hold our executable, and then copy the executable we built previously into the folder
define Package/nuistrover/install
		$(INSTALL_DIR) $(1)/usr/bin
		#$(INSTALL_DIR) $(1)/etc/init.d
		$(INSTALL_BIN) $(PKG_BUILD_DIR)/nuistrover $(1)/usr/bin
		#$(INSTALL_BIN) ./files/nuistrover.init $(1)/etc/init.d/nuistrover
endef
 
# This command is always the last, it uses the definitions and variables we give above in order to get the job done
$(eval $(call BuildPackage,nuistrover))
