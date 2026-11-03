# Integral calculator

A web application for evaluating integrals, built by a team of three for the *Software Engineering* course at the University of Warsaw (2022). The project plan (in Polish) is in [Software_Engineering___projekt.pdf](Software_Engineering___projekt.pdf), early notes in [OPIS.md](OPIS.md).

## Features

- Numerical definite integrals: composite trapezoid rule, Romberg's method, Gaussian quadrature (with and without a weight function)
- Integration treated as an ODE and solved with Runge-Kutta methods, returning the trajectory
- Exact indefinite integrals with SymPy
- Formulas rendered with MathJax and plotted with JSXGraph
- A gallery of computed integrals stored in a database

## Architecture

```
frontend/  React + TypeScript + React Bootstrap   ──HTTP──►   api/  Django REST Framework
                                                                │
                                              backend/  C++ numerical methods (pybind11)
```

- **[frontend](frontend)**: React and TypeScript single-page app with calculator settings, forms (react-hook-form), MathJax output and JSXGraph plots.
- **[api](api)**: Django REST API. The endpoints are listed in [api/README.md](api/README.md).
- **[backend](backend)**: numerical integration and ODE solvers in C++, using ExprTk to parse expressions, exposed to Python with pybind11 and built with CMake.

## Running

```bash
cd api && pip install -r requirements.txt && python manage.py runserver
cd frontend && npm install && npm start
```

The compiled C++ modules for Python 3.8 on Linux are included in `api/`; to rebuild them, build `backend/` with CMake.

## Team

Hubert Lubański, Szymon Jakubicz, Piotr Uznański.
