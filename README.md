# oop
class Product {
  constructor(id, name, price) {
    this.id = id;
    this.name = name;
    this.price = price;
  }
}

class ShoppingCartItem {
  constructor(product, quantity) {
    this.product = product;
    this.quantity = quantity;
  }

  getTotal() {
    return this.product.price * this.quantity;
  }
}

class ShoppingCart {
  constructor() {
    this.items = [];
  }

  addItem(item) {
    this.items.push(item);
  }

  removeItem(productId) {
    const index = this.items.findIndex(item => item.product.id === productId);
    if (index !== -1) {
      this.items.splice(index, 1);
    }
  }

  getTotal() {
    return this.items.reduce((total, item) => total + item.getTotal(), 0);
  }
}

const apple = new Product(1, "Apple", 2);
const banana = new Product(2, "Banana", 1);
const cart = new ShoppingCart();

cart.addItem(new ShoppingCartItem(apple, 3));
cart.addItem(new ShoppingCartItem(banana, 5));

console.log(cart.getTotal());

cart.removeItem(1);

console.log(cart.getTotal());
