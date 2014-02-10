# spree_better_payone

This is the Payone extenstion for Spree, to provide credit card payment via payone service.

## Installation

Add this line to your application's Gemfile:

    gem 'payone', git: 'https://github.com/procommerz/spree_better_payone'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install payone

## Usage

After complete bundle run this command, this will Copy & run migrations and copy a file `payone_config.rb` into your `config/initializers`.

    $ rails g payone:install
    
After complete installation add a payment method from admin UI for Payone by selecting `Spree::Gateway::PAYONE::CreditCard` form provider. And after this change the values of config variables to setup payone account according to your envirnoments in your `payone_config.rb` file.

You can provide support for any of the credit cards. The possiable values for `credit_card_types` config variables are shown below:

    Visa Card: V
    MasterCard: M
    Amex: A
    American Diners: D
    JCB: J
    Maestro Int.: O
    Discover: C
    Carte Bleue: B
    
To support more then one credit card use commas `,` between two.

    Payone.credit_card_types = 'v,m'
    
## Configuration

1. Before you begin

You'll need to have a Payone test account (https://pmi.pay1.de/).

2. Setup the Payment Method

Log in as an admin and add a new **Payment Method** (under Configuration), using following details:

**Name:** Payone

**Environment:** Development (or what ever environment you prefer)

**Active:** Yes

**Provider:** Spree::Gateway::PAYONE::CreditCard

Click **Create* , and now add your credentials in the screen that follows:

Now on your `payone_config.rb` file

**Merchant ID:** Merchant Id that is provided by payone

**Payment Portal Id:** Payment Portal Id of merchant

**Payment Portal Key:** Payment Portal key of merchant

**Sub Account Id:** Provide an alternative sub account id, that is registered in your payone merchant account

**Test Mode:** true (or false for Production)

**Currency Code:** Currency for the transation

**Credit Card Types:** Provide credit card keywords to support different card types

Save the file, restart your server and test the checkout process.


## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
