
<!-- README.md is generated from README.Rmd. Please edit that file -->

# trendminer <img src='man/figures/logo.png' align="right" height="138" />

<!-- badges: start -->

[![Travis build
status](https://travis-ci.com/alex23lemm/trendminer.svg?branch=master)](https://travis-ci.com/alex23lemm/trendminer)
[![Codecov test
coverage](https://codecov.io/gh/alex23lemm/trendminer/branch/master/graph/badge.svg)](https://codecov.io/gh/alex23lemm/trendminer?branch=master)
<!-- badges: end -->

trendminer is an R client for accessing selected endpoints of the
TrendMiner API available at <http://developer.trendminer.com/>.
TrendMiner is an industrial self-service analytics platform for
analyzing, monitoring and predicting time-series based process and asset
data.

## Installation

``` r
# install.packages("devtools")
devtools::install_github("alex23lemm/trendminer")
```

## Usage

Below are some things you can do after installing the package:

``` r
library(trendminer)

token <- tm_get_token()
token
#> List of 7
#>  $ access_token     : chr "0041147b-2ad6-43f2-9952-535df473bc13"
#>  $ token_type       : chr "bearer"
#>  $ expires_in       : int 37216
#>  $ scope            : chr "read"
#>  $ allowedHistorians: chr "ALL"
#>  $ userId           : chr "d891dff7-051d-4649-a389-029aa5b116de"
#>  $ expiration_date  : POSIXct[1:1], format: "2019-12-12 21:45:40"
#>  - attr(*, "class")= chr "tm_token"
```

## Authentication

All requests to the TrendMiner API require authentication using a valid
Bearer access token that is sent as part of the request headers.

Request tokens are obtained via OAuth2.0 using a resource owner password
credentials flow. Any client which likes to interact with the API needs
to collect the credentials from the user (username and password) and
passes them together with its own client credentials (client ID and
client secret) to the TrendMiner server using the `tm_get_token()`
function. The server responds with an access token which the user needs
to use for any subsequent API requests.

User credentials, client credentials and the TrendMiner base URL can be
passed as arguments to `tm_get_token()` for quick testing in interactive
mode. However, it is recommended to call `tm_get_token()` without
arguments. In this case `tm_get_token()` will fetch the credentials and
the TrendMiner base URL from the environment variables below which you
need to store in `.Renviron`. You can easily edit `.Renviron` using
`usethis::edit_r_environ()`.

``` r
TM_client_ID = YOUR_CLIENT_ID_HERE
TM_secret = YOUR_CLIENT_SECRET_HERE
TM_usr = YOUR_USER_NAME_HERE
TM_pwd = YOUR_USER_PASSWORD_HERE
TM_base_url = YOUR_TM_BASE_URL_HERE
```
