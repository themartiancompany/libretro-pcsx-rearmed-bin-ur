# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer:
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

_os="$( \
  uname \
    -o)"
_evmfs="true"
_pkgname="libretro-pcsx-rearmed"
_Pkg="PCSXReARMed"
_pkg="pcsx_rearmed"
pkgname="${_pkgname}-bin"
pkgver="r24l"
pkgrel=1
_pkgdesc=(
  "ARM optimized PCSX fork"
  "core for RetroArch."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'aarch64'
  'arm'
  'armv7l'
)
_http="https://github.com"
_ns="libretro"
url="${_http}/${_ns}/${_pkg}"
license=(
  'GPL2'
)
depends=(
  'retroarch'
)
if [[ "${_os}" != "GNU/Linux" ]] && \
   [[ "${_os}" == "Android" ]]; then
  depends+=(
    'inteppacman'
  )
fi
optdepends=(
)
[[ "${_os}" != "GNU/Linux" ]] && \
[[ "${_os}" == "Android" ]] && \
  optdepends+=(
  )
makedepends=(
  'coreutils'
  'evmfs'
)
checkdepends=(
)
provides=(
  "${_pkgname}=${pkgver}"
  "${_pkgname}-android=${pkgver}"
  "${_pkgname}-android-bin=${pkgver}"
)
conflicts=(
  "${_pkgname}"
  "${_pkgname}-android"
  "${_pkgname}-android-bin"
)
source=()
sha256sums=()
_lib="${_pkg}_libretro_android.so"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
if [[ "${_arch}" == "arm" || \
      "${_arch}" == "armv7l" ]]; then
  _lib_sum="c99da6071940ac1bd1a4704474ca3375796240eec60dc945f8c410fa8a9f41a6"
elif [[ "${_arch}" == "aarch64" ]]; then
  _lib_sum="190a0cd437d7a05aa0e25a468009fe81ad857ff43c9125a24a46387e4d76d23a"
fi
_evmfs_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_lib_sum}"
_lib_src="${_lib}.tar.xz::${_evmfs_uri}"
source+=(
  "${_lib_src}"
)
sha256sums+=(
  "${_lib_sum}"
)

validgpgkeys=(
)

package() {
  local \
    _dest_dir
  _dest_dir="/data/data/com.retroarch/cores"
  install \
    -dm755 \
    "${pkgdir}${_dest_dir}"
  install \
    -Dm644 \
    "${srcdir}/${_lib}" \
    "${pkgdir}/${_dest_dir}/${_lib}"
}

# vim: ft=sh syn=sh et
