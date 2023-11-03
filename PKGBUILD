pkgname=ifstat-rs
pkgver=1.0.0
pkgrel=1
pkgdesc="A program that shows network device speed"
arch=('x86_64')
url="https://github.com/vehlwn/ifstat-rs"
license=(ISC)
makedepends=(cargo)
source=("$pkgname-$pkgver.tar.gz::https://github.com/vehlwn/$pkgname/archive/$pkgver.tar.gz")
sha256sums=(SKIP)

prepare() {
    export RUSTUP_TOOLCHAIN=stable
    cd "$pkgname-$pkgver"
    cargo fetch --locked --target "$CARCH-unknown-linux-gnu"
}

build() {
    export RUSTUP_TOOLCHAIN=stable
    export CARGO_TARGET_DIR=target
    cd "$pkgname-$pkgver"
    cargo build --frozen --release --all-features
}

package() {
    cd "$pkgname-$pkgver"
    install -Dm0755 -t "$pkgdir/usr/bin/" "target/release/$pkgname"
}
