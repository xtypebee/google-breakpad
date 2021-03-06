# Nonstandard package files for distribution.
EXTRA_DIST =

# We may need to build our internally packaged gtest. If so, it will be
# included in the 'subdirs' variable.
SUBDIRS = $(subdirs)

# Scripts and utilities to be installed by 'make install'.
dist_bin_SCRIPTS = scripts/gmock_doctor.py
bin_SCRIPTS = scripts/gmock-config

# This is generated by the configure script, so clean it for distribution.
DISTCLEANFILES = scripts/gmock-config

# We define the global AM_CPPFLAGS as everything we compile includes from these
# directories.
AM_CPPFLAGS = $(GTEST_CPPFLAGS) -I$(srcdir)/include

# Build rules for libraries.
lib_LTLIBRARIES = lib/libgmock.la lib/libgmock_main.la

lib_libgmock_la_SOURCES = src/gmock-all.cc

pkginclude_HEADERS = include/gmock/gmock.h \
                     include/gmock/gmock-actions.h \
                     include/gmock/gmock-cardinalities.h \
                     include/gmock/gmock-generated-actions.h \
                     include/gmock/gmock-generated-function-mockers.h \
                     include/gmock/gmock-generated-matchers.h \
                     include/gmock/gmock-generated-nice-strict.h \
                     include/gmock/gmock-matchers.h \
                     include/gmock/gmock-more-actions.h \
                     include/gmock/gmock-printers.h \
                     include/gmock/gmock-spec-builders.h

pkginclude_internaldir = $(pkgincludedir)/internal
pkginclude_internal_HEADERS = \
  include/gmock/internal/gmock-generated-internal-utils.h \
  include/gmock/internal/gmock-internal-utils.h \
  include/gmock/internal/gmock-port.h

lib_libgmock_main_la_SOURCES = src/gmock_main.cc
lib_libgmock_main_la_LIBADD = lib/libgmock.la

# Build rules for tests. Automake's naming for some of these variables isn't
# terribly obvious, so this is a brief reference:
#
# TESTS -- Programs run automatically by "make check"
# check_PROGRAMS -- Programs built by "make check" but not necessarily run

TESTS=
check_PROGRAMS=
AM_LDFLAGS = $(GTEST_LDFLAGS)

# This exercises all major components of Google Mock.  It also
# verifies that libgmock works.
TESTS += test/gmock-spec-builders_test
check_PROGRAMS += test/gmock-spec-builders_test
test_gmock_spec_builders_test_SOURCES = test/gmock-spec-builders_test.cc
test_gmock_spec_builders_test_LDADD = $(GTEST_LIBS) lib/libgmock.la

# This tests using Google Mock in multiple translation units.  It also
# verifies that libgmock_main works.
TESTS += test/gmock_link_test
check_PROGRAMS += test/gmock_link_test
test_gmock_link_test_SOURCES = test/gmock_link_test.cc \
                               test/gmock_link2_test.cc \
                               test/gmock_link_test.h
test_gmock_link_test_LDADD = $(GTEST_LIBS) lib/libgmock_main.la

# Google Mock source files that we don't compile directly.
EXTRA_DIST += \
  src/gmock.cc \
  src/gmock-cardinalities.cc \
  src/gmock-internal-utils.cc \
  src/gmock-matchers.cc \
  src/gmock-printers.cc \
  src/gmock-spec-builders.cc

# C++ tests that we don't compile using autotools.
EXTRA_DIST += \
  test/gmock_all_test.cc \
  test/gmock-actions_test.cc \
  test/gmock-cardinalities_test.cc \
  test/gmock-generated-actions_test.cc \
  test/gmock-generated-function-mockers_test.cc \
  test/gmock-generated-internal-utils_test.cc \
  test/gmock-generated-matchers_test.cc \
  test/gmock-internal-utils_test.cc \
  test/gmock-matchers_test.cc \
  test/gmock-more-actions_test.cc \
  test/gmock-nice-strict_test.cc \
  test/gmock-port_test.cc \
  test/gmock-printers_test.cc \
  test/gmock_test.cc

# Python tests, which we don't run using autotools.
EXTRA_DIST += \
  test/gmock_test_utils.py \
  test/gmock_leak_test_.cc \
  test/gmock_leak_test.py \
  test/gmock_output_test_.cc \
  test/gmock_output_test.py \
  test/gmock_output_test_golden.txt

# Nonstandard package files for distribution.
EXTRA_DIST += \
    CHANGES \
    CONTRIBUTORS \
    make/Makefile

# Pump scripts for generating Google Mock headers.
# TODO(chandlerc@google.com): automate the generation of *.h from *.h.pump.
EXTRA_DIST += include/gmock/gmock-generated-actions.h.pump \
              include/gmock/gmock-generated-function-mockers.h.pump \
              include/gmock/gmock-generated-matchers.h.pump \
              include/gmock/gmock-generated-nice-strict.h.pump \
              include/gmock/internal/gmock-generated-internal-utils.h.pump

# Script for fusing Google Mock and Google Test source files.
EXTRA_DIST += \
    scripts/fuse_gmock_files.py \
    scripts/test/Makefile

# The Google Mock Generator tool from the cppclean project.
EXTRA_DIST += \
    scripts/generator/COPYING \
    scripts/generator/README \
    scripts/generator/README.cppclean \
    scripts/generator/cpp/__init__.py \
    scripts/generator/cpp/ast.py \
    scripts/generator/cpp/gmock_class.py \
    scripts/generator/cpp/keywords.py \
    scripts/generator/cpp/tokenize.py \
    scripts/generator/cpp/utils.py \
    scripts/generator/gmock_gen.py

# Microsoft Visual Studio 2005 projects.
EXTRA_DIST += \
    msvc/gmock.sln \
    msvc/gmock.vcproj \
    msvc/gmock_config.vsprops \
    msvc/gmock_link_test.vcproj \
    msvc/gmock_main.vcproj \
    msvc/gmock-spec-builders_test.vcproj \
    msvc/gmock_test.vcproj
