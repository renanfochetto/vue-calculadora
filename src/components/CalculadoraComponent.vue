<script>
export default {
  data() {
    return {
      resultado: '',
    };
  },
  methods: {
    calcular(tipo, valor) {
      if (tipo === 'acao') {
        if (valor === 'C') {
          this.resultado = '';
        } else if (['+', '-', '*', '/', '.'].includes(valor)) {
          this.resultado += valor;
        } else if (valor === '=') {
          try {
            this.resultado = eval(this.resultado);
          } catch {
            this.resultado = 'Erro';
          }
        }
      } else if (tipo === 'valor') {
        this.resultado += valor;
      }
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="row">
      <div class="col d-flex justify-content-center">
        <br />
        <div class="calculadora">
          <label for="resultado" class="visually-hidden">Resultado</label>
          <input id="resultado" type="text" class="form-control resultado" :value="resultado" placeholder="0" disabled aria-label="Campo de resultado" />

          <div class="row">
            <button aria-label="Limpar" @click="calcular('acao', 'C')" type="button" class="btn btn-dark btn-lg clear font-weight-light">C</button>
            <button aria-label="Divisão" @click="calcular('acao', '/')" type="button" class="btn btn-dark btn-lg font-weight-light">/</button>
            <button aria-label="Multiplicação" @click="calcular('acao', '*')" type="button" class="btn btn-dark btn-lg font-weight-light">x</button>
          </div>

          <div class="row">
            <button aria-label="7" @click="calcular('valor', '7')" type="button" class="btn btn-dark btn-lg font-weight-light">7</button>
            <button aria-label="8" @click="calcular('valor', '8')" type="button" class="btn btn-dark btn-lg font-weight-light">8</button>
            <button aria-label="9" @click="calcular('valor', '9')" type="button" class="btn btn-dark btn-lg font-weight-light">9</button>
            <button aria-label="Subtração" @click="calcular('acao', '-')" type="button" class="btn btn-dark btn-lg font-weight-light">-</button>
          </div>

          <div class="row">
            <button aria-label="4" @click="calcular('valor', '4')" type="button" class="btn btn-dark btn-lg font-weight-light">4</button>
            <button aria-label="5" @click="calcular('valor', '5')" type="button" class="btn btn-dark btn-lg font-weight-light">5</button>
            <button aria-label="6" @click="calcular('valor', '6')" type="button" class="btn btn-dark btn-lg font-weight-light">6</button>
            <button aria-label="Adição" @click="calcular('acao', '+')" type="button" class="btn btn-dark btn-lg font-weight-light">+</button>
          </div>

          <div class="row">
            <button aria-label="1" @click="calcular('valor', '1')" type="button" class="btn btn-dark btn-lg font-weight-light">1</button>
            <button aria-label="2" @click="calcular('valor', '2')" type="button" class="btn btn-dark btn-lg font-weight-light">2</button>
            <button aria-label="3" @click="calcular('valor', '3')" type="button" class="btn btn-dark btn-lg font-weight-light">3</button>
            <button aria-label="Resultado" @click="calcular('acao', '=')" type="button" class="btn btn-dark btn-lg enter">=</button>
          </div>

          <div class="row" style="margin-top: -60px">
            <button aria-label="0" @click="calcular('valor', '0')" type="button" class="btn btn-dark zero btn-lg font-weight-light">0</button>
            <button aria-label="Decimal" @click="calcular('acao', '.')" type="button" class="btn btn-dark btn-lg font-weight-light">.</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped>

.calculadora {
    border: solid 0.0625rem #000;
    padding: 1.5rem;
    background-color: #3e3e3e;
    border-radius: 0.625rem;
    box-shadow: 0.0625rem 0.0625rem 0.3125rem #000;
}

.visually-hidden {
    position: absolute;
    width: 1px;
    height: 1px;
    margin: -1px;
    padding: 0;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    border: 0;
}

.btn {
    width: 3.75rem;
    height: 3.125rem;
    margin: 0.3125rem;
    box-shadow: 0.0625rem 0.0625rem 0.0625rem #000;
    background-color: #4caf50;
    color: #fff;
}

.clear {
    width: 8.125rem;
    background-color: #f44336;
    color: #fff;
}

.enter {
    height: 6.875rem;
    background-color: #2196f3;
    color: #fff;
}

.zero {
    width: 8.125rem;
}

.resultado {
    text-align: right;
    font-size: 1.25rem;
    margin-top: 0.625rem;
    margin-bottom: 1.25rem;
    border: solid 0.0625rem #000;
    box-shadow: 0.0625rem 0.0625rem 0.0625rem #000;
    background-color: #fff;
    color: #000;
}

</style>