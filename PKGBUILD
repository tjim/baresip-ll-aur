pkgname=baresip-ll
pkgver=0.4.4
pkgrel=1
pkgdesc="A portable and modular SIP User-Agent with audio and video support"
arch=('i686' 'x86_64')
url="http://www.creytiv.com/"
license=('custom:BSD')
depends=("librem>=0.4.3")

_gitroot="https://github.com/tjim/baresip-ll"
_gitname="baresip-ll"

build() {
  cd $srcdir
  msg 'Connecting to GIT server...'
  if [ -d "$_gitname" ] ; then
    (cd "$_gitname"; git pull origin)
    msg 'The local files are updated.'
  else
    git clone "$_gitroot" "$_gitname"
  fi
  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  cd "$_gitname"
  make PREFIX=/usr
}

package() {
  cd "$srcdir/$_gitname"
  make DESTDIR="$pkgdir" install

  # license
  install -Dm644 docs/COPYING \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
